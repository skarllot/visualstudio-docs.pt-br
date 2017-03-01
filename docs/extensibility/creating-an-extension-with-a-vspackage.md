---
title: "Criando uma extensão com um VSPackage | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
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
ms.openlocfilehash: 8592e003810fda491b2e0b8c8ff8530a2e7c8004
ms.lasthandoff: 02/22/2017

---
# <a name="creating-an-extension-with-a-vspackage"></a>Criando uma extensão com um VSPackage
Este passo a passo mostra como criar um projeto do VSIX e adicione um item de projeto de VSPackage. Nós usaremos o VSPackage para obter o serviço de Shell de interface do usuário para mostrar uma caixa de mensagem.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Criando um VSPackage  
  
1.  Crie um projeto do VSIX chamado **FirstPackage**. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual c# / extensibilidade**.  
  
2.  Quando o projeto é aberto, adicione um modelo de item de pacote do Visual Studio chamado **FirstPackage**. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **Visual Studio Package**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **FirstPackage.cs**.  
  
3.  Compile o projeto e iniciar a depuração.  
  
     A instância experimental do Visual Studio é exibida. Para obter mais informações sobre a instância experimental, consulte [a instância Experimental](../extensibility/the-experimental-instance.md).  
  
4.  Na instância experimental, abra o **ferramentas / extensões e atualizações** janela. Você deve ver o **FirstPackage** extensão aqui. (Se você abrir **extensões e atualizações** em sua instância de trabalho do Visual Studio, você não verá **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Carregar o VSPackage  
 Neste momento a extensão não for carregado, porque não há nada que impeça a carga. Geralmente, você pode carregar uma extensão ao interagir com sua interface do usuário (clicando em um comando de menu, abrindo uma janela de ferramentas), ou especificando que o VSPackage deverá ser carregado em um contexto específico de interface do usuário. Para obter mais informações sobre como carregar contextos VSPackages e interface do usuário, consulte [VSPackages Carregando](../extensibility/loading-vspackages.md). Para este procedimento, mostraremos como carregar um VSPackage quando uma solução estiver aberta.  
  
1.  Abra o arquivo FirstPackage.cs. Procure a declaração da classe FirstPackage. Substitua os atributos existentes pelo seguinte:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Vamos adicionar uma mensagem que nos informa que o VSPackage foi carregado. Usamos o método de Initialize () do VSPackage para fazer isso, porque você pode obter serviços do Visual Studio somente depois que o VSPackage foi colocado no local. (Para obter mais informações sobre serviços, consulte [como: obter um serviço](../extensibility/how-to-get-a-service.md).) Substitua o método Initialize () de FirstPackage pelo código que obtém a <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>de serviço, obtém o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>interface e chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> </xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
    ```c#  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Compile o projeto e iniciar a depuração. A instância experimental aparece.  
  
4.  Abra uma solução na instância experimental. Você deve ver uma caixa de mensagem que diz **primeiro pacote dentro Initialize ()**.
