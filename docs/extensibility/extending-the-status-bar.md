---
title: Estendendo a barra de Status | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 23
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
ms.openlocfilehash: d2df69a523074ed936d31deb31abe18299439159
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-status-bar"></a>Estendendo a barra de Status
Você pode usar a barra de status do Visual Studio na parte inferior do IDE para exibir informações.  
  
 Quando você estende a barra de status, você pode exibir informações e interface do usuário em quatro regiões: a região de comentários, a barra de progresso, a região de animação e a região de designer. A região de comentários permite exibir texto e realce o texto exibido. A barra de progresso mostra o progresso incremental para operações de curta duração, como salvar um arquivo. A região de animação exibe uma animação em loop continuamente para operações de longa execução ou operação de tamanho indeterminado, como criar vários projetos em uma solução. E a região designer mostra o número de linha e coluna do local do cursor.  
  
 Você pode obter a barra de status, usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>interface (da <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>service).</xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> </xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> Além disso, qualquer objeto situado em um quadro de janela pode se registrar como um objeto de cliente da barra de status ao implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Sempre que uma janela é ativada, o Visual Studio consulta o objeto situado em janela para o `IVsStatusbarUser` interface. Se encontrado, ele chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>método na interface da retornado e o objeto pode atualizar a barra de status de dentro desse método.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> Documentar o windows, por exemplo, pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>método para atualizar as informações na região designer quando eles se tornam ativos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>  
  
 Os procedimentos a seguir pressupõem que você aprendeu como criar um projeto do VSIX e adicione um comando de menu personalizado. Para obter informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Modificando a barra de Status  
 Este procedimento mostra como definir e obter o texto, exibir texto estático e realce o texto exibido na região de comentários da barra de status.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Leitura e gravação para a barra de status  
  
1.  Crie um projeto do VSIX chamado **TestStatusBarExtension** e adicione um comando de menu chamado **TestStatusBarCommand**.  
  
2.  Em TestStatusBarCommand.cs, substitua o código de método do manipulador de comando (MenuItemCallback) com o seguinte:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3.  Compile o código e iniciar a depuração.  
  
4.  Abra o **ferramentas** menu na instância experimental do Visual Studio. Clique o **TestStatusBarCommand invocar** botão.  
  
     Você verá que o texto na barra agora leituras de status **"Que acabamos de escrever para a barra de status."** e a caixa de mensagem que aparece tem o mesmo texto.  
  
#### <a name="updating-the-progress-bar"></a>Atualizando a barra de progresso  
  
1.  Neste procedimento, mostraremos como inicializar e atualizar a barra de progresso.  
  
2.  Abra o arquivo TestStatusBarCommand.cs e substitua o método MenuItemCallback com o código a seguir:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3.  Compile o código e iniciar a depuração.  
  
4.  Abra o **ferramentas** menu na instância experimental do Visual Studio. Clique em **TestStatusBarCommand invocar** botão.  
  
     Você verá que o texto na barra agora leituras de status **"Escrevendo para a barra de progresso".** Você também deve ver a barra de progresso é atualizado a cada segundo por 20 segundos. Depois que a barra de status e a barra de progresso são desmarcadas.  
  
#### <a name="displaying-an-animation"></a>Exibindo uma animação  
  
1.  A barra de status exibe uma animação de loop que indica uma operação de longa duração (por exemplo, criando vários projetos em uma solução). Se você não vir essa animação, verifique se você tem as devidas **Ferramentas / opções** configurações:  
  
     Vá para o **Ferramentas/opções / geral** guia e desmarque **ajustar automaticamente a experiência visual com base no desempenho do cliente**. Em seguida, marque a opção subpasta **habilitar experiência visual do cliente avançado**. Agora, você poderá visualizar a animação quando você compila o projeto em sua instância experimental do Visual Studio.  
  
     Neste procedimento, podemos exibir a animação padrão do Visual Studio que representa a criação de um projeto ou solução.  
  
2.  Abra o arquivo TestStatusBarCommand.cs e substitua o método MenuItemCallback com o código a seguir:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3.  Compile o código e iniciar a depuração.  
  
4.  Abra o **ferramentas** menu na instância experimental do Visual Studio e clique em **TestStatusBarCommand invocar**.  
  
     Quando você vir a caixa de mensagem, você também verá a animação na barra de status na extrema direita. Quando você fechar a caixa de mensagem, a animação desaparece.
