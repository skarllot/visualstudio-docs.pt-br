---
title: Adicionar um Menu a barra de menus do Visual Studio | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 51
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
ms.openlocfilehash: abecc0466f19aa9487ae4bdc1fc16a65a2b8123d
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Adicionar um Menu a barra de menus do Visual Studio
Este passo a passo mostra como adicionar um menu a barra de menus do ambiente de desenvolvimento integrado (IDE) do Visual Studio. A barra de menus do IDE contém categorias de menu como **arquivo**, **editar**, **exibição**, **janela**, e **ajuda**.  
  
 Antes de adicionar um novo menu para a barra de menus do Visual Studio, considere se os comandos devem ser colocados dentro de um menu existente. Para obter mais informações sobre o posicionamento de comando, consulte [Menus e comandos para o Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Menus são declarados no arquivo VSCT do projeto. Para obter mais informações sobre menus e arquivos. VSCT, consulte [comandos, Menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Ao concluir este passo a passo, você pode criar um menu chamado **TestMenu** que contém um comando.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é fornecido como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Criando um projeto do VSIX que tem um modelo de item de comando de personalizada  
  
1.  Crie um projeto do VSIX chamado `TopLevelMenu`. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual C#** / **extensibilidade**.  Para obter mais informações, consulte [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Quando o projeto é aberto, adicione um modelo de item de comando personalizada chamado **TestCommand**. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c# / extensibilidade** e selecione **comando personalizado**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para **TestCommand.cs**.  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Criando um Menu na barra de menus do IDE  
  
#### <a name="to-create-a-menu"></a>Para criar um menu  
  
1.  Em **Solution Explorer**, abra TestCommandPackage.vsct.  
  
     No final do arquivo, há um \<símbolos > nó que contém vários \<GuidSymbol > nós. No nó chamado guidTestCommandPackageCmdSet, adicione um novo símbolo, da seguinte maneira:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Criar vazia \<Menus > nó a \<comandos > nó antes \<grupos >. No \<Menus > nó, adicione um \<Menu > nó, da seguinte maneira:  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     O `guid` e `id` valores do menu especificam o conjunto de comandos e menu específico no conjunto de comando.  
  
     O `guid` e `id` valores do pai posicionar o menu na seção da barra de menu do Visual Studio que contém os menus ferramentas e suplementos.  
  
     O valor de `CommandName` cadeia de caracteres que especifica que o texto deve aparecer no item de menu.  
  
3.  No \<grupos > seção, localize o \<grupo > e altere o \<pai > elemento para apontar para o menu que acabamos de adicionar:  
  
    ```c#  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Isso faz parte do grupo do novo menu.  
  
4.  Encontre o `Buttons` seção. Observe que o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelo de pacote gerou um `Button` elemento que tem pai definido como `MyMenuGroup`. Como resultado, esse comando aparecerá no menu.  
  
## <a name="building-and-testing-the-extension"></a>Criar e testar a extensão  
  
1.  Compile o projeto e iniciar a depuração. Uma instância da instância experimental deve aparecer.  
  
2.  A barra de menus na instância experimental deve conter um **TestMenu** menu.  
  
3.  Sobre o **TestMenu** menu, clique em **invocar comando de teste**.  
  
     Uma caixa de mensagem deve aparecer e exibir a mensagem "TestCommand pacote dentro do TopLevelMenu.TestCommand.MenuItemCallback()". Isso indica que o novo comando funcione.  
  
## <a name="see-also"></a>Consulte também  
 [Barras de ferramentas, Menus e comandos](../extensibility/internals/commands-menus-and-toolbars.md)
