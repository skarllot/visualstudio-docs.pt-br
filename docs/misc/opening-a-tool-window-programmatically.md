---
title: "Abrindo uma janela de ferramentas programaticamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "janelas de ferramentas, criar de forma programática"
ms.assetid: 0017441e-7aa3-4a61-9939-57af11d90d97
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Abrindo uma janela de ferramentas programaticamente
Janelas de ferramentas normalmente são abertas, clicando em um comando em um menu ou pressionando a tecla de atalho equivalente. No entanto, você talvez precise abrir uma janela de ferramentas programaticamente, como o manipulador de comandos.  
  
 Para abrir uma janela de ferramenta no VSPackage gerenciado que oferece, use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A>. Para abrir uma janela de ferramenta em outro VSPackage, use <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.FindToolWindow%2A>. Em ambos os casos, a janela da ferramenta é criada conforme necessário.  
  
 O código a seguir é retirado do exemplo c\# Reference.ToolWindow.  
  
### Para abrir uma janela de ferramentas programaticamente  
  
1.  Crie o painel de janela de ferramenta, quadro e o VSPackage que implementá\-las. Para obter mais informações, consulte [Adicionar uma janela de ferramentas](../extensibility/adding-a-tool-window.md).  
  
2.  Adicionar o <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> para o VSPackage que fornece a ele.  
  
    ```c#  
    [ProvideToolWindow(typeof(PersistedWindowPane), Style = VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideMenuResource(1000, 1)] [MsVsShell.DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\8.0Exp")] [PackageRegistration(UseManagedResourcesOnly = true)] [Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")] // your package will have a different GUID public class PackageToolWindow : Package {  
    ```  
  
     Esse registros a janela da ferramenta PersistedWindowPane para ser aberto como encaixada **Solution Explorer**. Para obter mais informações, consulte [Registrando uma janela de ferramentas](../extensibility/registering-a-tool-window.md).  
  
3.  Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para localizar o painel de janela de ferramenta ou criá\-lo se ele ainda não existir.  
  
    ```vb#  
    ' Get the 1 (index 0) and only instance of our tool window. ' If it does not already exist it will get created. Dim pane As MsVsShell.ToolWindowPane = Me.FindToolWindow(GetType(PersistedWindowPane), 0, True) If pane Is Nothing Then End If  
  
    ```  
  
    ```c#  
    // Get the 1 (index 0) and only instance of our tool window. // If it does not already exist it will get created. MsVsShell.ToolWindowPane pane =     this.FindToolWindow(typeof(PersistedWindowPane), 0, true); if (pane == null) {  
    ```  
  
4.  Obter o quadro de janela de ferramenta do painel de janela de ferramenta.  
  
    ```vb#  
    Dim frame As IVsWindowFrame = TryCast(pane.Frame, IVsWindowFrame) If frame Is Nothing Then End If  
  
    ```  
  
    ```c#  
    IVsWindowFrame frame = pane.Frame as IVsWindowFrame; if (frame == null) {  
    ```  
  
5.  Mostra a janela da ferramenta.  
  
    ```vb#  
    ' Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show())  
  
    ```  
  
    ```c#  
    // Bring the tool window to the front and give it focus ErrorHandler.ThrowOnFailure(frame.Show());  
    ```