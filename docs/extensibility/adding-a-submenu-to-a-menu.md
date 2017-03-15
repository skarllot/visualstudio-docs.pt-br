---
title: Adicionando um Submenu a um Menu | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
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
ms.openlocfilehash: 70fa57e23b06ed5ad7336ce7b8eeefda1a9fd1cf
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-submenu-to-a-menu"></a>Adicionando um Submenu a um Menu
Este passo a passo se baseia a demonstração em [adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , mostrando como adicionar um submenu para o **TestMenu** menu.  
  
 Um submenu é um menu secundário que aparece em outro menu. Um submenu pode ser identificado pela seta que acompanha seu nome. Clicando no nome faz com que o submenu e os comandos a serem exibidos.  
  
 Este passo a passo cria um submenu em um menu na barra de menus do Visual Studio e coloca um novo comando no submenu. Passo a passo também implementa o novo comando.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Adicionando um Submenu a um Menu  
  
1.  Siga as etapas em [adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) para criar o item de menu e projeto. As etapas neste passo a passo presumem que o nome do projeto VSIX é `TopLevelMenu`.  
  
2.  Abra TestCommandPackage.vsct. No `<Symbols>` seção, adicione um `<IDSymbol>` elemento para o submenu, um para o grupo de submenu e um para o comando, tudo no `<GuidSymbol>` nó chamado "guidTopLevelMenuCmdSet". Esse é o mesmo nó que contém o `<IDSymbol>` elemento para o menu de nível superior.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Adicionar o submenu recém-criado para o `<Menus>` seção.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     O par GUID/ID do pai Especifica o grupo de menu que foi gerado em [adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), e é um filho do menu de nível superior.  
  
4.  Adicionar o grupo de menus definido na etapa 2 para o `<Groups>` seção e torná-lo um filho do submenu.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Adicione um novo `<Button>` elemento para o `<Buttons>` seção para definir o comando criado na etapa 2 como um item no submenu.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  Compile a solução e inicie a depuração. Você deve ver a instância experimental.  
  
7.  Clique em **TestMenu** para ver um novo submenu chamado **submenu**. Clique em **submenu** para abrir o submenu e verá um novo comando, **teste subcomando**. Observe que clicar **teste subcomando** não faz nada.  
  
## <a name="adding-a-command"></a>Adicionando um comando  
  
1.  Abra TestCommand.cs e adicione o seguinte ID de comando após o ID de comando existente.  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Adicione o comando subpropriedades. Localize o construtor de comando. Adicione as seguintes linhas imediatamente após a chamada para o `AddCommand` método.  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     O `SubItemCallback` manipulador de comando será definido posteriormente. O construtor deve ficar assim:  
  
    ```c#  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  Adicione SubItemCallback(). Esse é o método que é chamado quando o comando novo no submenu é clicado.  
  
    ```c#  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  Compile o projeto e iniciar a depuração. A instância experimental deve aparecer.  
  
5.  Sobre o **TestMenu** menu, clique em **submenu** e, em seguida, clique em **teste subcomando**. Uma caixa de mensagem deve aparecer e exibir o texto, "Teste comando dentro TestCommand.SubItemCallback()".  
  
## <a name="see-also"></a>Consulte também  
 [Adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Barras de ferramentas, Menus e comandos](../extensibility/internals/commands-menus-and-toolbars.md)
