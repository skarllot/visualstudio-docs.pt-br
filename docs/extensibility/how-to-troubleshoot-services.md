---
title: "Como: solucionar problemas de serviços | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
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
ms.openlocfilehash: c8e4aaabcf8672217341e7519d8e9354bac8cd90
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-troubleshoot-services"></a>Como: solucionar problemas de serviços
Há vários problemas comuns que podem ocorrer ao tentar obter um serviço:  
  
-   O serviço não está registrado com [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   O serviço é solicitado pelo tipo de interface e não pelo tipo de serviço.  
  
-   O VSPackage solicitando o serviço não tem sido localizado.  
  
-   O provedor de serviço errada é usado.  
  
 Se o serviço solicitado não pode ser obtido, a chamada para <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>retorna null.</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Você sempre deve testar null após a solicitação em um serviço:  
  
```c#  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Para solucionar problemas de um serviço  
  
1.  Examine o registro do sistema para ver se o serviço foi registrado corretamente. Para obter mais informações, consulte [Registrando serviços](../misc/registering-services.md).  
  
     O fragmento de arquivo. reg a seguir mostra como o serviço de SVsTextManager pode ser registrado:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     No exemplo acima, o número de versão é a versão do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 12.0 ou 14.0, a chave {F5E7E71D-1401-11d1-883B-0000F87579D2} é o identificador de serviço (SID) do serviço, SVsTextManager, e o valor padrão {F5E7E720-1401-11d1-883B-0000F87579D2} é o GUID do Gerenciador de texto VSPackage, que fornece o serviço do pacote.  
  
2.  Use o tipo de serviço e não o tipo de interface ao chamar GetService. Ao solicitar um serviço de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package>extrai a GUID do tipo.</xref:Microsoft.VisualStudio.Shell.Package> Um serviço não será encontrado se as seguintes condições existirem:  
  
    1.  Um tipo de interface é passado para GetService em vez do tipo de serviço.  
  
    2.  Nenhum GUID explicitamente é atribuído à interface. Portanto, o sistema cria um padrão GUID para um objeto, conforme necessário.  
  
3.  Certifique-se de que o VSPackage solicitando o serviço foi localizado. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sites um VSPackage depois construí-la e antes de chamar <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>  
  
     Se você tiver código em um construtor de VSPackage que precisa de um serviço, mova-o para o método Initialize.  
  
4.  Certifique-se de que você está usando o provedor de serviço correta.  
  
     Nem todos os provedores de serviço são iguais. O provedor de serviços que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passa para uma janela de ferramenta é diferente daquele que ele passa a um VSPackage. O provedor de serviços de janela de ferramenta conhece <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, mas não sabe sobre <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>.</xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> </xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Você pode chamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>para obter um provedor de serviços de VSPackage de dentro de uma janela de ferramenta.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
     Se uma janela de ferramentas hospeda um controle de usuário ou qualquer outro contêiner de controle, o contêiner será colocado no local pelo modelo de componente do Windows e não terá acesso a qualquer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serviços. Você pode chamar <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>para obter um provedor de serviços de VSPackage dentro de um contêiner de controle.</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Lista de serviços disponíveis](../extensibility/internals/list-of-available-services.md)   
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Conceitos básicos do serviço](../extensibility/internals/service-essentials.md)
