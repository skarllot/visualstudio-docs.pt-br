---
title: "Abrindo uma janela de ferramenta dinâmica | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 21
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
ms.openlocfilehash: 13a1bca132e8994c7b265cdf77dee5a9a24da8ac
ms.lasthandoff: 02/22/2017

---
# <a name="opening-a-dynamic-tool-window"></a>Abrindo uma janela de ferramenta dinâmica
Janelas de ferramentas normalmente são abertas de um comando em um menu ou uma tecla de atalho equivalente. Às vezes, no entanto, talvez seja necessário uma janela de ferramenta que abre sempre que um contexto específico de interface do usuário se aplica e fecha quando o contexto de interface do usuário não se aplica. Janelas de ferramenta como esses são chamadas *dinâmico* ou *automática visível*.  
  
> [!NOTE]
>  Para obter uma lista de contextos de interface do usuário predefinidas, consulte <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.</xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> Para o  
  
 Se desejar abrir uma janela de ferramenta dinâmico na inicialização e é possível que a criação falhar, você deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx>da interface e testar as condições de falha no <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A>método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> Para o shell sabe que você tenha uma janela de ferramenta dinâmica que deve ser aberta na inicialização, você deve adicionar o `SupportsDynamicToolOwner` valor (definida como 1) em seu registro de pacote. Esse valor não é parte do padrão <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>portanto, você deve criar um atributo personalizado para adicionar o proprietário.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Para obter mais informações sobre atributos personalizados, consulte [usando um atributo personalizado do registro para registrar uma extensão](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>para abrir uma janela de ferramenta.</xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> A janela da ferramenta é criada, conforme necessário.  
  
> [!NOTE]
>  Uma janela de ferramenta dinâmica pode ser encerrada pelo usuário. Se você quiser criar um comando de menu para que o usuário pode reabrir a janela da ferramenta, o comando de menu deve ser habilitado no mesmo contexto de interface do usuário que abre a janela da ferramenta e desabilitado caso contrário.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Para abrir uma janela de ferramenta dinâmica  
  
1.  Crie um projeto do VSIX chamado **DynamicToolWindow** e adicione um modelo de item da janela de ferramenta chamado **DynamicWindowPane.cs**. Para obter mais informações, consulte [criando uma extensão com uma janela da ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  No arquivo DynamicWindowPanePackage.cs, localize a declaração DynamicWindowPanePackage. Adicione o <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>e os atributos de T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute para registrar a janela da ferramenta.</xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Isso registra a janela da ferramenta denominada DynamicWindowPane como uma janela transitória que não é persistida quando o Visual Studio é fechado e reaberto. DynamicWindowPane é aberta sempre que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string>se aplica e fechado caso contrário.</xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string>  
  
3.  Compile o projeto e iniciar a depuração. A instância experimental deve aparecer. Você não verá a janela da ferramenta.  
  
4.  Abra um projeto na instância experimental. A janela da ferramenta deve aparecer.
