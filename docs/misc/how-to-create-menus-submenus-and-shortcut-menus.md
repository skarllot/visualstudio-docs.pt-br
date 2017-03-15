---
title: "Como: criar Menus, SubMenus e Menus de atalho | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barras de comando, arquitetura"
  - "menus, criando"
  - "menus, arquitetura"
  - "comandos, menus"
  - "menus"
ms.assetid: 62004fd9-7f99-4f00-8d01-1dde53e23dbb
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# Como: criar Menus, SubMenus e Menus de atalho
Para adicionar um menu ao ambiente de desenvolvimento integrado \(IDE\) do Visual Studio, um VSPackage deve usar o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] arquitetura para menus do grupo de comando. Um grupo de comandos menu permite o compartilhamento de comandos por componentes e o IDE. Para obter mais informações sobre menus do grupo de comandos, consulte [Como os VSPackages adicionar elementos de Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Em VSPackages, menus são definidos no [Menus](../extensibility/menus-element.md) seção de um arquivo. VSCT. Um arquivo. VSCT define menus, barras de ferramentas, grupos e comandos. Um comando é o que um usuário clica para realizar uma função. Um grupo é um contêiner para comandos. Um menu é um contêiner para grupos. Para criar um menu básico, você deve criar um menu, um grupo de comandos e pelo menos um comando.  
  
 Há três maneiras básicas que pode ser exibido um menu no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Como um menu na barra de menus principal.  
  
-   Como um submenu de outro menu.  
  
-   Como um menu de atalho \(normalmente exibido por um clique\).  
  
 Este tópico mostra como criar cada tipo de menu. As instruções a seguir também mostra como fazer isso:  
  
-   [Adicionar um Menu a barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
  
-   [Adicionando um Submenu a um Menu](../extensibility/adding-a-submenu-to-a-menu.md)  
  
-   [Adicionar um Menu de atalho em uma janela de ferramenta](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)  
  
### Para criar um menu, submenu ou menu de atalho  
  
1.  Em seu projeto, clique duas vezes no arquivo. VSCT para abri\-lo no editor.  
  
     Se seu projeto não tem um arquivo. VSCT, adicione uma. Se você estiver criando um pacote usando o modelo de pacote do Visual Studio, selecione **comando de Menu**; isso irá gerar um arquivo. VSCT.  
  
2.  No `Symbols` seção, localize o [GuidSymbol](../extensibility/guidsymbol-element.md) elemento que contém os grupos e comandos.  
  
3.  Criar um [IDSymbol](../extensibility/idsymbol-element.md) elemento para cada menu, grupo ou comando que você deseja adicionar, conforme mostrado no exemplo a seguir.  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     O `name` atributos a `GuidSymbol` e `IDSymbol` elementos fornecem o par de GUID:ID para cada novo menu, o grupo ou o comando. O `GUID` representa um conjunto de comandos que está definido para o VSPackage. Você pode definir vários conjuntos de comandos. Cada par GUID:ID deve ser exclusivo.  
  
4.  Definir o novo menu no `Menus` seção, da seguinte maneira:  
  
    1.  Definir o `guid` e `id` campos para corresponder GUID:ID do novo menu.  
  
    2.  Definir o `priority` atributo.  
  
         O `priority` atributo é usado pelo arquivo. VSCT para determinar o local do menu entre os outros objetos no grupo pai.  
  
         Menus que têm valores de prioridade mais baixa são exibidos antes de menus que têm valores de prioridade mais alta. Valores de prioridade duplicados são permitidos, mas a posição relativa dos menus que têm a mesma prioridade é determinada pela ordem na qual os VSPackages são processados em tempo de execução e ordem não pode ser predeterminada. Omitindo o `priority` atributo define seu valor como 0.  
  
         Não defina uma prioridade para um menu de atalho, como seu posicionamento é determinado pelo código que o chama.  
  
    3.  Para menus e submenus, definir o `type` atributo `Menu`, que descreve um menu típico. Para menus de atalho, defina o `type` atributo `Context`.  
  
         Para obter descrições dos outros tipos de menu válido, como barras de ferramentas e menu controladores, consulte [Elemento de menu](../extensibility/menu-element.md).  
  
    4.  Na definição de menu, criar um [cadeias de caracteres](../extensibility/strings-element.md) seção que contém uma [ButtonText](../extensibility/buttontext-element.md) elemento para conter o nome do menu como ele aparece no IDE e um [CommandName](../extensibility/commandname-element.md) elemento para conter o nome do comando que é usado para acessar o menu no **comando** janela.  
  
         Se a cadeia de caracteres de texto do botão inclui o caractere '&', o usuário poderá abrir o menu pressionando a tecla ALT mais o caractere ou imediatamente após o '&'.  
  
    5.  Adicione sinalizadores de comando, conforme apropriado, para alterar a aparência e o comportamento do menu. Para fazer isso, adicione uma [CommandFlag](../extensibility/command-flag-element.md) elemento na definição de menu. Para obter mais informações, consulte [Elemento de sinalizador de comando](../extensibility/command-flag-element.md).  
  
5.  Defina o pai do menu. Para um menu padrão ou o submenu, fazer isso de uma das maneiras a seguir, dependendo do seu projeto:  
  
    -   No `Menu` elemento, criar uma [pai](../extensibility/parent-element.md) elemento e defina seu `guid` e `id` campos GUID:ID do grupo que irá hospedar o menu, também conhecido como o *grupo pai primário*. O grupo pai pode ser um grupo que você criou no `Symbols` seção, um grupo de outro pacote ou um grupo a partir do IDE. Por exemplo, para adicionar o menu para a barra de menu de nível superior do IDE, próximo a **ferramentas** menu, definir o pai para guidSHLMainMenu:IDG\_VS\_MM\_TOOLSADDINS.  
  
         O exemplo a seguir mostra um menu que aparecerá na barra de menus do Visual Studio.  
  
         [!CODE [TopLevelMenu#01](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#01)]  
  
    -   Você pode omitir o `Parent` elemento se o menu deve ser posicionados usando o posicionamento de comando. Criar um [CommandPlacements](../extensibility/commandplacements-element.md) seção antes do `Symbols` seção e adicione um [CommandPlacement](../extensibility/commandplacement-element.md) elemento que tem o GUID:ID de menu, uma prioridade e um pai, conforme mostrado no exemplo a seguir.  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         Criar vários posicionamentos de comandos que têm o mesmo GUID:ID e pais diferentes faz com que um menu seja exibido em vários locais. Para obter mais informações, consulte [Elemento CommandPlacements](../extensibility/commandplacements-element.md).  
  
     Um menu padrão deve ter um grupo na barra de menus do Visual Studio como seu pai. Para um submenu, o pai deve ser um grupo em outro menu \(ou em uma barra de ferramentas ou outro tipo de menu\). Para um menu ou submenu a ser exibido, ele deve hospedar um grupo que contenha pelo menos um comando ativo ou ter o `AlwaysCreate` comando sinalizador definido.  
  
     Menus de atalho não ter pais ou posicionamentos de comandos. Em vez disso, deve ser ativados no código. Normalmente, um menu de atalho é ativado em resposta a um botão direito do mouse em uma superfície de controle. O exemplo a seguir define um menu de atalho.  
  
     [!CODE [ButtonGroup#06](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#06)]  
  
6.  No [grupos](../extensibility/groups-element.md) seção, crie uma [grupo](../extensibility/group-element.md) elemento para conter os comandos que deverão ser exibidas no menu. O `Symbols` seção deve incluir uma entrada que tem o mesmo GUID:ID como o novo `Group` elemento.  
  
    1.  Defina a prioridade do grupo de forma que ele será exibido no local desejado no menu.  
  
         Os limites de cada grupo no menu serão exibido como linhas horizontais.  
  
    2.  Defina o pai para esse novo grupo para o GUID:ID do menu que você criou. Isso coloca o grupo de comandos no menu.  
  
     O grupo no exemplo a seguir aparece no menu de nível superior que foi mostrado no exemplo anterior.  
  
     [!CODE [TopLevelMenu#02](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#02)]  
  
     Menus podem conter comandos e submenus. Um submenu \(às vezes conhecido como um menu em cascata\) é apenas um menu, mas que é adicionado ao grupo do outro menu e é exposta somente quando outro menu é invocado. Colocando o menu é mostrado no exemplo a seguir em um grupo no menu de nível superior, ele se torna um submenu.  
  
     [!CODE [TopLevelMenu#06](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#06)]  
  
7.  Adicionar comandos ao menu criando entradas de comando na [botões](../extensibility/buttons-element.md) seção e a definição do pai de cada um deles GUID:ID do seu grupo. Cada [botão](../extensibility/button-element.md) elemento deve ter uma GUID:ID que corresponde a uma entrada no `Symbols` seção.  
  
     Use o `priority` atributo de cada entrada de botão para especificar a ordem na qual os comandos aparecem no grupo.  
  
     O exemplo a seguir define um comando que será exibido no menu de nível superior.  
  
     [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
     Para obter mais informações sobre itens de menu e botões, consulte [Elemento de botão](../extensibility/button-element.md).  
  
     Para obter informações sobre como implementar os comandos de menu no código, consulte [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md) ou a guias passo a passo mencionada anteriormente neste tópico.  
  
### Para ativar um menu de atalho  
  
1.  Obter GUID:ID no menu de atalho. Por padrão, o modelo de pacote cria um `GuidList` classe em um arquivo PkgCmdID.cs para manter o GUID do conjunto de comandos. O modelo também cria um `PkgCmdIdList` classe em um arquivo PkgCmdId.cs para manter o inteiro de valores de ID de comandos que são declarados no modelo. Menus de atalho e comandos adicionais devem ser declarados após o modelo. O exemplo a seguir mostra essas declarações.  
  
     [!CODE [TWShortcutMenu#12](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#12)]  
  
     Esta etapa pode ser omitida se os valores GUID e ID serão usados diretamente. No entanto, é recomendável que você defina os valores para facilitar a leitura.  
  
2.  Anexe a um manipulador de eventos. Normalmente, menus de atalho anexado para o botão direito do mouse de uma superfície de controle, conforme mostrado no exemplo a seguir.  
  
     [!CODE [TWShortcutMenu#43](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#43)]  
  
     O <xref:System.Windows.Forms.Control.PointToScreen%2A> método converte a posição do clique, que é em relação ao controle, em uma posição na tela. O <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> método exibe o menu de atalho.  
  
     O arquivo que contém o manipulador de eventos deve incluir o <xref:System.ComponentModel.Design> namespace para acessar o <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> classe e o <xref:Microsoft.VisualStudio.Shell> namespace para acessar o <xref:System.ComponentModel.Design.IMenuCommandService> interface.  
  
     [!CODE [TWShortcutMenu#41](../CodeSnippet/VS_Snippets_VSSDK/twshortcutmenu#41)]  
  
## Consulte também  
 [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Referência de esquema XML VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Estendendo Menus e comandos](../extensibility/extending-menus-and-commands.md)