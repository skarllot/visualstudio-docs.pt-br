---
title: Adicionar um controlador de Menu a uma barra de ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
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
ms.openlocfilehash: f5cfe142d92cac88eae5c5108721cc11e98b199d
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Adicionar um controlador de Menu a uma barra de ferramentas
Este passo a passo o [adicionar uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) passo a passo e mostra como adicionar um controlador de menu na barra de ferramentas de janela de ferramenta. As etapas mostradas aqui também podem ser aplicadas à barra de ferramentas que é criado no [adicionar uma barra de ferramentas](../extensibility/adding-a-toolbar.md) passo a passo.  
  
 Um controlador de menu é um controle de divisão. O lado esquerdo do controlador de menu mostra o último comando e pode ser executada clicando nele. À direita do controlador de menu é uma seta que, quando clicado, abre uma lista de comandos adicionais. Quando você clica em um comando na lista, o comando é executado, e substitui o comando no lado esquerdo do controlador de menu. Dessa forma, o controlador de menu opera como um botão de comando que sempre mostra o comando usado por último em uma lista.  
  
 Controladores de menu podem ser exibidas nos menus, mas geralmente são usados nas barras de ferramentas.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Criando um controlador de Menu  
  
#### <a name="to-create-a-menu-controller"></a>Para criar um controlador de menu  
  
1.  Siga os procedimentos descritos em [adicionar uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) para criar uma janela de ferramenta que tem uma barra de ferramentas.  
  
2.  No TWTestCommandPackage.vsct, vá para a seção de símbolos. No elemento GuidSymbol chamado **guidTWTestCommandPackageCmdSet**, declare o controlador de menu, grupo de controlador de menu e três itens de menu.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Na seção de Menus, após a última entrada de menu, defina o controlador de menu como um menu.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     O `TextChanges` e `TextIsAnchorCommand` sinalizadores deve ser incluídas para permitir que o controlador de menu refletir o último comando selecionado.  
  
4.  Os grupos de seção, após a última entrada de grupo, adicione o grupo de controlador de menu.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Configurando o controlador de menu como o pai, todos os comandos colocados nesse grupo aparecerá no controlador de menu. O `priority` atributo for omitido, que define como o valor padrão de 0, pois ela será o único grupo no controlador de menu.  
  
5.  Na seção de botões, após a última entrada de botão, adicione um elemento de botão para cada um dos seus itens de menu.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  Neste ponto, você pode examinar o controlador de menu. Compile o projeto e iniciar a depuração. Você deve ver a instância experimental.  
  
    1.  Sobre o **exibição / outras janelas** menu, abrir **teste ToolWindow**.  
  
    2.  O controlador de menu é exibido na barra de ferramentas na janela da ferramenta.  
  
    3.  Clique na seta à direita do controlador menu para ver os três comandos possíveis.  
  
     Observe que, quando você clica em um comando, o título do controlador menu muda para exibir esse comando. Na próxima seção, adicionaremos o código para ativar esses comandos.  
  
## <a name="implementing-the-menu-controller-commands"></a>Implementando os comandos de Menu controlador  
  
1.  No TWTestCommandPackageGuids.cs, adicione as IDs de comando para os itens de três menu após o IDs de comando existente.  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  Em TWTestCommand.cs, adicione o seguinte código na parte superior da classe TWTestCommand.  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  No construtor TWTestCommand, após a última chamada para o `AddCommand` método, adicione código para rotear os eventos para cada comando pelos mesmos manipuladores.  
  
    ```c#  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Adicione um manipulador de eventos à classe TWTestCommand para marcar o comando selecionado como verificado.  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Adicione um manipulador de eventos que exibe uma caixa de mensagem quando o usuário seleciona um comando no controlador de menu:  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>Testar o controlador de Menu  
  
1.  Compile o projeto e iniciar a depuração. Você deve ver a instância experimental.  
  
2.  Abra o **teste ToolWindow** no **exibição / outras janelas** menu.  
  
     O controlador de menu é exibido na barra de ferramentas na janela da ferramenta e exibe **MC Item 1**.  
  
3.  Clique no botão de controlador de menu à esquerda da seta.  
  
     Você verá três itens, o primeiro deles é selecionado e tem uma caixa de realce em torno de seu ícone. Clique em **MC Item 3**.  
  
     Uma caixa de diálogo é exibida com a mensagem **você selecionou o controlador de Menu Item 3**. Observe que a mensagem correspondente ao texto no botão de controlador do menu. O botão de menu controlador agora exibe **MC Item 3**.  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando uma barra de ferramentas para uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Adicionando uma barra de ferramentas](../extensibility/adding-a-toolbar.md)
