---
title: Alterar o texto de um comando de Menu | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ba6acf73a84a7a6ff5ae0c513bc5e8cf74111719
ms.contentlocale: pt-br
ms.lasthandoff: 02/22/2017

---
# <a name="changing-the-text-of-a-menu-command"></a>Alterar o texto de um comando de Menu
As etapas a seguir mostram como alterar o rótulo de texto de um comando de menu usando o <xref:System.ComponentModel.Design.IMenuCommandService>service.</xref:System.ComponentModel.Design.IMenuCommandService>  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Alterar um rótulo de comando de menu com o IMenuCommandService  
  
1.  Crie um projeto do VSIX chamado `MenuText` com um comando de menu chamado **ChangeMenuText**. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  No arquivo .vstc, adicione o `TextChanges` sinalizar para o comando de menu, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  No arquivo ChangeMenuText.cs, crie um manipulador de eventos será chamado antes do comando de menu é exibido.  
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     Você também pode atualizar o status do comando de menu nesse método, alterando o <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, e <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A>Propriedades de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>objeto.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand> </xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> </xref:System.ComponentModel.Design.MenuCommand.Checked%2A> </xref:System.ComponentModel.Design.MenuCommand.Visible%2A>  
  
4.  No construtor ChangeMenuText, substitua o código de inicialização e o posicionamento de comando original com o código que cria um <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>(em vez de uma `MenuCommand`) que representa o comando de menu, adiciona o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>manipulador de eventos e fornece o menu de comando para o serviço de comando de menu.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> </xref:Microsoft.VisualStudio.Shell.OleMenuCommand>  
  
     Aqui está o que deve se parecer com:  
  
    ```c#  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  Compile o projeto e iniciar a depuração. A instância experimental do Visual Studio é exibida.  
  
6.  Sobre o **ferramentas** menu, você verá um comando chamado **ChangeMenuText invocar**.  
  
7.  Clique no comando. Você verá a caixa de mensagem anunciando que MenuItemCallback foi chamado. Quando você fechar a caixa de mensagem, você verá o nome do comando no menu de ferramentas agora está **novo texto**.

