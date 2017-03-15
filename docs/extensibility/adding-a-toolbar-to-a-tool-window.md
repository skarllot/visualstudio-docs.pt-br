---
title: Adicionando uma barra de ferramentas para uma janela de ferramentas | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 48
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
ms.openlocfilehash: 80f8d2e3d689b05680c5d43a0d4b26f17d9a88ce
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Adicionando uma barra de ferramentas para uma janela de ferramenta
Este passo a passo mostra como adicionar uma barra de ferramentas para uma janela de ferramenta.  
  
 Uma barra de ferramentas é uma faixa horizontal ou vertical que contém botões associados a comandos. O comprimento da barra de ferramentas em uma janela de ferramenta é sempre o mesmo que a largura ou altura da janela de ferramenta, dependendo de onde a barra de ferramentas está ancorada.  
  
 Barras de ferramentas no IDE, ao contrário de uma barra de ferramentas em uma janela de ferramenta deve ser encaixada e não pode ser movida ou personalizada. Se o VSPackage é escrito em código umanaged, a barra de ferramentas pode ser encaixada em qualquer canto.  
  
 Para obter mais informações sobre como adicionar uma barra de ferramentas, consulte [adicionar uma barra de ferramentas](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Criando uma barra de ferramentas para uma janela de ferramentas  
  
1.  Crie um projeto do VSIX chamado `TWToolbar` que possui um comando menu chamado **TWTestCommand** e uma janela de ferramenta chamada **TestToolWindow**. Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md) e [criando uma extensão com uma janela da ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md). Você precisa adicionar o modelo de item de comando antes de adicionar o modelo de janela de ferramenta.  
  
2.  Em TWTestCommandPackage.vsct, procure a seção símbolos. No nó GuidSymbol chamado guidTWTestCommandPackageCmdSet declare uma barra de ferramentas e um grupo de ferramentas, da seguinte maneira.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  Na parte superior do `Commands` seção, crie um `Menus` seção. Adicione um `Menu` elemento para definir a barra de ferramentas.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Barras de ferramentas não podem ser aninhadas como submenus. Portanto, não é necessário atribuir um pai. Além disso, você não precisa definir uma prioridade, porque o usuário pode mover as barras de ferramentas. Normalmente, o posicionamento inicial de uma barra de ferramentas é definido por meio de programação, mas as alterações subsequentes pelo usuário são mantidas.  
  
4.  Na seção grupos, defina um grupo para conter os comandos da barra de ferramentas.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  Na seção de botões, altere o pai do elemento de botão existente para o grupo de barra de ferramentas para que a barra de ferramentas será exibida.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Por padrão, se uma barra de ferramentas não tem nenhum comando, ele não aparecerá.  
  
     Porque a nova barra de ferramentas não é automaticamente adicionada para a janela da ferramenta, a barra de ferramentas deve ser adicionada explicitamente. Isso é abordado na próxima seção.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Adicionando a barra de ferramentas para a janela da ferramenta  
  
1.  Em TWTestCommandPackageGuids.cs, adicione as seguintes linhas.  
  
    ```c#  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  Em TestToolWindow.cs, adicione a seguinte instrução using.  
  
    ```c#  
    using System.ComponentModel.Design;  
    ```  
  
3.  No construtor TestToolWindow, adicione a seguinte linha.  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Teste a barra de ferramentas na janela da ferramenta  
  
1.  Compile o projeto e iniciar a depuração. A instância experimental do Visual Studio deve aparecer.  
  
2.  Sobre o **exibição / outras janelas** menu, clique em **ToolWindow de teste** para exibir a janela da ferramenta.  
  
     Você verá uma barra de ferramentas (ele se parece com o ícone padrão) na parte superior esquerda da janela de ferramenta, logo abaixo do título.  
  
3.  Na barra de ferramentas, clique no ícone para exibir a mensagem **TWTestCommandPackage em TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Consulte também  
 [Adicionando uma barra de ferramentas](../extensibility/adding-a-toolbar.md)
