---
title: "Criar e gerenciar caixas de diálogo modais | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
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
ms.openlocfilehash: 1bb0372ab217847f91b1cdeeb8cf2915379e2f66
ms.lasthandoff: 02/22/2017

---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Criar e gerenciar caixas de diálogo modais
Quando você cria uma caixa de diálogo modal dentro do Visual Studio, você deve certificar-se de que a janela pai da caixa de diálogo está desabilitada enquanto a caixa de diálogo é exibida e reativar a janela pai depois que a caixa de diálogo é fechada. Se você não fizer isso, você pode receber o erro: "Microsoft Visual Studio não pode desligar porque uma caixa de diálogo modal está ativa. Feche a caixa de diálogo e tente novamente."  
  
 Há duas maneiras de fazer isso. A maneira recomendada, se você tiver uma caixa de diálogo do WPF é derivá-la de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, em seguida, chame <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A>para exibir a caixa de diálogo.</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Se você fizer isso, você não precisa gerenciar o estado modal da janela pai.  
  
 Se a caixa de diálogo não for WPF, ou para algum outro motivo, você não pode derivar sua caixa de diálogo classe de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, você deve obter o pai da caixa de diálogo chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A>e gerenciar o estado modal, ao chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A>método com um parâmetro de 0 (FALSO) antes de exibir a caixa de diálogo e chamando o método novamente com um parâmetro de 1 (verdadeiro) depois de fechar a caixa de diálogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Criar uma caixa de diálogo derivada de DialogWindow  
  
1.  Crie um projeto do VSIX chamado **OpenDialogTest** e adicione um comando de menu chamado **OpenDialog**. Para obter mais informações sobre como fazer isso, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Para usar o <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>classe, adicione referências aos assemblies a seguir (na guia estrutura do **adicionar referência** caixa de diálogo):</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System. XAML  
  
3.  Em OpenDialog.cs, adicione o seguinte `using` instrução:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Declare uma classe denominada **TestDialogWindow** que deriva de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:</xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>  
  
    ```c#  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Para poder minimizar e maximizar a caixa de diálogo, definir <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>e <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A>como true:</xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> </xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A>  
  
    ```c#  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  No **OpenDialog.ShowMessageBox** método, substitua o código existente pelo seguinte:  
  
    ```c#  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Crie e execute o aplicativo. A instância experimental do Visual Studio deve aparecer. Sobre o **ferramentas** menu da instância experimental, você verá um comando chamado **OpenDialog invocar**. Quando você clica nesse comando, você deve ver a janela de diálogo. Você deve ser capaz de minimizar e maximizar a janela.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Criando e gerenciando uma caixa de diálogo não derivada de DialogWindow  
  
1.  Para este procedimento, você pode usar o **OpenDialogTest** solução criada no procedimento anterior, com as mesmas referências de assembly.  
  
2.  Adicione o seguinte `using` declarações:  
  
    ```c#  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Crie uma classe denominada **TestDialogWindow2** que deriva de <xref:System.Windows.Window>:</xref:System.Windows.Window>  
  
    ```c#  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Adicione uma referência privada para <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Adicione um construtor que define a referência à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>  
  
    ```c#  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  No **OpenDialog.ShowMessageBox** método, substitua o código existente pelo seguinte:  
  
    ```c#  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  Crie e execute o aplicativo. Sobre o **ferramentas** menu, você verá um comando chamado **OpenDialog invocar**. Quando você clica nesse comando, você deve ver a janela de diálogo.
