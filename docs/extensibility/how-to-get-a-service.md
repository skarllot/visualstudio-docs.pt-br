---
title: "Como: obter um serviço | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f66c7e1f01c8d8eb69c6718314890bfb02cccc17
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-get-a-service"></a>Como: obter um serviço
Geralmente, você precisa obter serviços do Visual Studio para acessar recursos diferentes. Em geral, um serviço do Visual Studio fornece uma ou mais interfaces que você pode usar. Você pode obter a maioria dos serviços de um VSPackage.  
  
 Qualquer VSPackage que deriva de <xref:Microsoft.VisualStudio.Shell.Package>e que tenha sido colocado corretamente pode solicitar qualquer serviço global.</xref:Microsoft.VisualStudio.Shell.Package> Como a classe Package implementa <xref:System.IServiceProvider>, qualquer VSPackage que deriva de pacote também é um provedor de serviços.</xref:System.IServiceProvider>  
  
 Quando o Visual Studio carregará um <xref:Microsoft.VisualStudio.Shell.Package>, ele passa um <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>do objeto para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>método durante a inicialização.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Package> Isso é chamado de *localização* VSPackage. A classe de pacote encapsula esse provedor de serviços e fornece o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>método para obter serviços.</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtendo um serviço de um VSPackage inicializado  
  
1.  Cada extensão do Visual Studio inicia com um projeto de implantação do VSIX que conterá os ativos de extensão. Criar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto VSIX chamado `GetServiceExtension`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Agora, adicione um modelo de item de comando personalizada chamado **GetServiceCommand**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **comando personalizado**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **GetServiceCommand.cs**. Para obter mais informações sobre como criar um comando personalizado, [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  Em GetServiceCommand.cs, remova o corpo do método MenuItemCommand e adicione o seguinte código:  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Esse código obtém um serviço SVsActivityLog e converte-o em uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>interface, que pode ser usado para gravar no log de atividade.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Para obter um exemplo, consulte [como: usar o Log de atividade](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Compile o projeto e iniciar a depuração. A instância experimental aparece.  
  
5.  No menu Ferramentas da instância experimental, encontre o **GetServiceCommand invocar** botão. Quando você clica nesse botão, você verá uma caixa de mensagem que diz **encontrado o serviço de log de atividade.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtendo um serviço de um contêiner de controle ou janela de ferramenta  
 Às vezes, talvez seja necessário obter um serviço em uma janela de ferramenta ou controle de contêiner que não foi localizado, senão foi colocado no local com um provedor de serviços não sabe sobre o serviço que você deseja. Por exemplo, você talvez queira gravar no log de atividade de dentro de um controle.  
  
 Estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>método depende de um provedor de serviços em cache que é inicializado na primeira vez que qualquer VSPackage derivado de <xref:Microsoft.VisualStudio.Shell.Package>é localizado.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 Como o construtor de VSPackage é chamado antes do VSPackage é localizado, serviços globais são normalmente disponíveis de dentro do construtor de VSPackage. Consulte [como: resolver serviços](../extensibility/how-to-troubleshoot-services.md) para uma solução alternativa.  
  
 Aqui está um exemplo da forma de obter um serviço em uma janela de ferramenta ou outro elemento de VSPackage não.  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Obtendo um serviço do objeto DTE  
 Você também pode obter serviços de <xref:EnvDTE.DTEClass>objeto.</xref:EnvDTE.DTEClass> No entanto, você deve obter o objeto DTE como um serviço de um VSPackage ou chamando estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>método.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 O objeto DTE implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que pode ser usada para consultar um serviço usando <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.</xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 Eis como obter um serviço do objeto DTE.  
  
```c#  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como: fornecer um serviço](../extensibility/how-to-provide-a-service.md)   
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)
