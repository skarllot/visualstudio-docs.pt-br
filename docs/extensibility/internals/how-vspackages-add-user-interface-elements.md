---
title: "Como os VSPackages adicionar elementos de Interface do usuário | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 60
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
ms.openlocfilehash: 6bf44a2b1fa029753c4b3c00f911070a2132bb75
ms.lasthandoff: 02/22/2017

---
# <a name="how-vspackages-add-user-interface-elements"></a>Como os VSPackages adicionar elementos de Interface do usuário
Um VSPackage pode adicionar elementos interface do usuário (UI), por exemplo, menus, barras de ferramentas e janelas para o Visual Studio por meio do arquivo. VSCT de ferramentas.  
  
 Você pode encontrar as diretrizes de design para elementos de interface do usuário em [diretrizes de experiência de usuário do Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>A arquitetura de tabela de comando do Visual Studio  
 Conforme observado, a arquitetura do comando tabela suporta os princípios de arquitetura precedente. Os princípios por trás de abstrações, estruturas de dados e ferramentas da arquitetura de tabela do comando são as seguintes:  
  
-   Há três tipos básicos de itens: menus, comandos e grupos. Menus podem ser expostos na interface do usuário como menus, submenus, barras de ferramentas ou janelas de ferramenta. Comandos são procedimentos que o usuário pode executar no IDE, e eles podem ser expostos como itens de menu, botões, caixas de listagem ou outros controles. Grupos são contêineres para menus e comandos.  
  
-   Cada item é especificado por uma definição que descreve o item, sua prioridade em relação a outros itens e os sinalizadores de modificam seu comportamento.  
  
-   Cada item possui um posicionamento que descreve o pai do item. Um item pode ter vários pais, para que ele pode aparecer em vários locais na interface do usuário.  
  
     Cada comando deve ter um grupo como pai, mesmo se ele for o único filho desse grupo. Cada menu padrão também deve ter um grupo pai. Barras de ferramentas e janelas de ferramenta atuam como suas próprias pais. Um grupo pode ter como seu pai, a barra de menu principal do Visual Studio, ou qualquer menu, a barra de ferramentas ou a janela da ferramenta.  
  
### <a name="how-items-are-defined"></a>Como os itens são definidos  
 . VSCT arquivos são formatados em XML. Um arquivo. VSCT define os elementos da interface do usuário para um pacote e determina onde os elementos são exibidos no IDE. Cada menu, um grupo ou um comando no pacote é atribuído pela primeira vez um GUID e ID de `Symbols` seção. No restante do VSCT arquivo, cada menu, o comando e o grupo é identificado por sua combinação de GUID e ID. O exemplo a seguir mostra um típico `Symbols` seção geradas pelo modelo de pacote do Visual Studio quando um **o comando de Menu** selecionadas no modelo.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 O elemento de nível superior a `Symbols` seção é o [GuidSymbol elemento](../../extensibility/guidsymbol-element.md). `GuidSymbol`elementos mapeiam nomes para os GUIDs são usados pelo IDE para identificar os pacotes e suas partes de componente.  
  
> [!NOTE]
>  GUIDs são gerados automaticamente pelo modelo de pacote do Visual Studio. Você também pode criar um GUID exclusivo, clicando em **criar GUID** sobre o **ferramentas** menu.  
  
 A primeira `GuidSymbol` elemento, "guid [PackageName] Pkg", é o GUID do pacote. Esse é o GUID que é usado pelo Visual Studio para carregar o pacote. Normalmente, ele não tem elementos filho.  
  
 Por convenção, os menus e comandos são agrupados em um segundo `GuidSymbol` elemento, "guid [PackageName] CmdSet", e bitmaps em um terceiro `GuidSymbol` elemento, "guidImages". Você não precisa seguir essa convenção, mas cada menu, o grupo, o comando e o bitmap devem ser um filho de um `GuidSymbol` elemento.  
  
 No segundo `GuidSymbol` elemento, que representa o conjunto de comandos de pacote, são várias `IDSymbol` elementos. Cada [IDSymbol elemento](../../extensibility/idsymbol-element.md) mapeia um nome para um valor numérico e podem representar um menu, um grupo ou um comando que faz parte do conjunto de comandos. O `IDSymbol` elementos na terceira `GuidSymbol` elemento representam bitmaps que podem ser usados como ícones para comandos. Como pares GUID ID devem ser exclusivos em um aplicativo, não há dois filhos do mesmo `GuidSymbol` elemento pode ter o mesmo valor.  
  
### <a name="menus-groups-and-commands"></a>Menus, grupos e comandos  
 Quando um menu, o grupo ou o comando tem um GUID e ID, podem ser adicionado ao IDE. Cada elemento de interface do usuário deve ter as seguintes ações:  
  
-   Um `guid` que corresponde ao nome do atributo de `GuidSymbol` elemento que o elemento de interface do usuário é definido em.  
  
-   Um `id` atributo que corresponde ao nome do associado `IDSymbol` elemento.  
  
     Juntos, o `guid` e `id` atributos compõem o *assinatura* do elemento da interface do usuário.  
  
-   Um `priority` atributo que determina o posicionamento do elemento da interface do usuário em seu menu pai ou grupo.  
  
-   A [elemento pai](../../extensibility/parent-element.md) com `guid` e `id` atributos que especificam a assinatura do menu pai ou do grupo.  
  
#### <a name="menus"></a>Menus  
 Cada menu é definido como um [elemento Menu](../../extensibility/menu-element.md) no `Menus` seção. Menus devem ter `guid`, `id`, e `priority` atributos e um `Parent` elemento e também os seguintes atributos adicionais e filhos:  
  
-   Um `type` atributo que especifica se o menu deve aparecer no IDE como um tipo de menu ou uma barra de ferramentas.  
  
-   A [elemento cadeias de caracteres](../../extensibility/strings-element.md) que contém um [ButtonText elemento](../../extensibility/buttontext-element.md), que especifica o título de menu no IDE e um [CommandName elemento](../../extensibility/commandname-element.md), que especifica o nome que é usado no **comando** janela para acessar o menu.  
  
-   Sinalizadores opcionais. A [comando sinalizador elemento](../../extensibility/command-flag-element.md) pode aparecer em uma definição de menu para alterar sua aparência ou comportamento no IDE.  
  
 Cada `Menu` elemento deve ter um grupo como seu pai, a menos que ele seja um elemento acoplável como uma barra de ferramentas. Um menu acoplável é seu próprio pai. Para obter mais informações sobre menus e valores para o `type` de atributo, consulte o [elemento Menu](../../extensibility/menu-element.md) documentação.  
  
 O exemplo a seguir mostra um menu que aparece na barra de menus do Visual Studio, ao lado de **ferramentas** menu.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Grupos  
 Um grupo é um item que é definido na `Groups` seção do arquivo. VSCT. Os grupos são apenas contêineres. Eles não aparecem no IDE exceto como uma linha divisória em um menu. Portanto, uma [grupo elemento](../../extensibility/group-element.md) é definida somente por sua assinatura, a prioridade e o pai.  
  
 Um grupo pode ter um menu, o outro grupo ou o próprio como pai. No entanto, o pai é normalmente um menu ou barra de ferramentas. No menu do exemplo anterior é um filho de `IDG_VS_MM_TOOLSADDINS` grupo e esse grupo é um filho da barra de menu do Visual Studio. O grupo no exemplo a seguir é um filho do menu no exemplo anterior.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Porque faz parte de um menu, esse grupo normalmente conteria comandos. No entanto, ele também pode conter outros menus. Isso é como submenus são definidas, conforme mostrado no exemplo a seguir.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Comandos  
 Um comando que é fornecido para o IDE é definido como um [elemento Button](../../extensibility/button-element.md) ou um [combinação elemento](../../extensibility/combo-element.md). Para aparecer em um menu ou uma barra de ferramentas, o comando deve ter um grupo como pai.  
  
##### <a name="buttons"></a>Botões  
 Botões são definidos na `Buttons` seção. Qualquer item de menu, botão ou outro elemento que um usuário clica para executar um único comando é considerado um botão. Alguns tipos de botão também podem incluir a funcionalidade de lista. Botões têm o mesmo necessárias e os atributos opcionais que têm menus, e também pode ter um [elemento de ícone](../../extensibility/icon-element.md) que especifica o GUID e a ID do bitmap que representa o botão no IDE. Para obter mais informações sobre botões e seus atributos, consulte o [elemento botões](../../extensibility/buttons-element.md) documentação.  
  
 O botão no exemplo a seguir é um filho do grupo no exemplo anterior e apareceria no IDE como um item de menu no menu pai do grupo.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Combinações  
 Combinações são definidas na `Combos` seção. Cada `Combo` elemento representa uma caixa de lista suspensa no IDE. A caixa de listagem pode ou não ser gravável por usuários, dependendo do valor da `type` atributo da caixa de combinação. Combinações têm os mesmos elementos e têm comportamento botões e também pode ter os seguintes atributos adicionais:  
  
-   Um `defaultWidth` atributo que especifica a largura em pixels.  
  
-   Um `idCommandList` atributo que especifica uma lista que contém os itens que são exibidos na caixa de listagem. A lista de comando deve ser declarada no mesmo `GuidSymbol` nó que contém a caixa de combinação.  
  
 O exemplo a seguir define um elemento de combinação.  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>Bitmaps  
 Os comandos que serão exibidos junto com um ícone devem incluir um `Icon` elemento se refere a um bitmap usando seu GUID e ID. Cada bitmap é definido como um [Bitmap elemento](../../extensibility/bitmap-element.md) no `Bitmaps` seção. Os únicos atributos para necessários um `Bitmap` definição são `guid` e `href`, que aponta para o arquivo de origem. Se o arquivo de origem é uma faixa de recursos, um **usedList** atributo também é necessário, para listar as imagens disponíveis na faixa de. Para obter mais informações, consulte o [Bitmap elemento](../../extensibility/bitmap-element.md) documentação.  
  
### <a name="parenting"></a>Domínio pai  
 As regras a seguir controlam como um item pode chamar outro item como seu pai.  
  
|Elemento|Definidos nesta seção da tabela de comando|Podem ser contidos (como um pai ou posicionamento no `CommandPlacements` seção ou ambos)|Pode conter (conhecido como um pai)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Grupo|[Elemento Groups](../../extensibility/groups-element.md), o IDE, outros VSPackages|Um menu, um grupo, o próprio item|Menus, grupos e comandos|  
|Menu|[Elemento de menus](../../extensibility/menus-element.md), o IDE, outros VSPackages|1 para *n* grupos|0 a *n* grupos|  
|Barra de ferramentas|[Elemento de menus](../../extensibility/menus-element.md), o IDE, outros VSPackages|O próprio item|0 a *n* grupos|  
|Item de menu|[Botões de elemento](../../extensibility/buttons-element.md), o IDE, outros VSPackages|1 para *n* grupos, o próprio item|-0 para *n* grupos|  
|Botão|[Botões de elemento](../../extensibility/buttons-element.md), o IDE, outros VSPackages|1 para *n* grupos, o próprio item||  
|Combinação|[Elemento de combinações](../../extensibility/combos-element.md), o IDE, outros VSPackages|1 para *n* grupos, o próprio item||  
  
### <a name="menu-command-and-group-placement"></a>Menu, Command e posicionamento do grupo  
 Um menu, o grupo ou o comando pode aparecer em mais de um local no IDE. Para um item seja exibido em vários locais, ele deve ser adicionado para o `CommandPlacements` seção como um [CommandPlacement elemento](../../extensibility/commandplacement-element.md). Qualquer menu, o grupo ou o comando pode ser adicionado como o posicionamento de um comando. No entanto, as barras de ferramentas não podem ser posicionadas dessa maneira porque eles não podem aparecer em vários locais contextuais.  
  
 Posicionamentos de comandos têm `guid`, `id`, e `priority` atributos. O GUID e ID devem corresponder do item que está posicionado. O `priority` atributo controla o posicionamento do item em relação a outros itens. Quando o IDE mescla dois ou mais itens que têm a mesma prioridade, suas posições são indefinidas porque o IDE não garante que recursos do pacote são lidos na mesma ordem toda vez que o pacote é construído.  
  
 Se um menu ou grupo é exibido em vários locais, todos os filhos do menu ou grupo será exibido em cada instância.  
  
## <a name="command-visibility-and-context"></a>Visibilidade de comando e o contexto  
 Quando vários VSPackages são instalados, uma profusão de menus, itens de menu e barras de ferramentas pode truncar o IDE. Para evitar esse problema, você pode controlar a visibilidade dos elementos de interface de usuário individuais usando *as restrições de visibilidade* e sinalizadores de comando.  
  
##### <a name="visibility-constraints"></a>Restrições de visibilidade  
 Uma restrição de visibilidade é definida como um [VisibilityItem elemento](../../extensibility/visibilityitem-element.md) no `VisibilityConstraints` seção. Uma restrição de visibilidade define contextos específicos de interface do usuário em que o item de destino está visível. Um menu ou um comando que está incluído nesta seção só é visível quando um dos contextos definidos está ativo. Se um menu ou comando não é referenciado nesta seção, está sempre visível por padrão. Esta seção não se aplica a grupos.  
  
 `VisibilityItem`elementos devem ter três atributos, da seguinte maneira: o `guid` e `id` do elemento de interface do usuário de destino, e `context`. O `context` atributo especifica quando o item de destino serão visível e utiliza qualquer contexto de interface de usuário válido como seu valor. As constantes de contexto da interface do usuário para o Visual Studio são membros de <xref:Microsoft.VisualStudio.VSConstants>classe.</xref:Microsoft.VisualStudio.VSConstants> Cada `VisibilityItem` elemento pode ter o valor de apenas um contexto. Para aplicar um contexto de segundo, crie um segundo `VisibilityItem` elemento que aponta para o mesmo item, conforme mostrado no exemplo a seguir.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>Sinalizadores de comando  
 Os seguintes sinalizadores de comando podem afetar a visibilidade dos menus e comandos que se aplicam.  
  
 AlwaysCreate  
 Menu será criado mesmo que ele não tem grupos ou botões.  
  
 Válida para:`Menu`  
  
 CommandWellOnly  
 Aplica esse sinalizador se o comando não aparecer no menu de nível superior e você deseja disponibilizar para a personalização do shell adicionais, por exemplo, associação a uma chave. Depois que o VSPackage é instalado, o usuário pode personalizar esses comandos abrindo o **opções** caixa de diálogo e, em seguida, editando o posicionamento de comando na **teclado ambiente** categoria. Não afeta o posicionamento em menus de atalho, barras de ferramentas, controladores de menu ou submenus.  
  
 Válido para: `Button`,`Combo`  
  
 DefaultDisabled  
 Por padrão, o comando é desabilitado se o VSPackage que implementa o comando não está carregado ou não foi chamado do método QueryStatus.  
  
 Válido para: `Button`,`Combo`  
  
 DefaultInvisible  
 Por padrão, o comando é invisível se o VSPackage que implementa o comando não está carregado ou não foi chamado do método QueryStatus.  
  
 Deve ser combinada com a `DynamicVisibility` sinalizador.  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 DynamicVisibility  
 A visibilidade do comando pode ser alterada por meio do método QueryStatus ou um GUID que está incluído no contexto de `VisibilityConstraints` seção.  
  
 Aplica-se aos comandos que aparecem nos menus, não em barras de ferramentas. Itens de nível superior da barra de ferramentas podem ser desabilitadas, mas não ocultas, quando o sinalizador OLECMDF_INVISIBLE é retornado do método QueryStatus.  
  
 Em um menu, esse sinalizador indica também que ele deve ser automaticamente ocultado quando seus membros estão ocultos. Esse sinalizador é geralmente atribuído aos submenus, como menus de nível superior já têm esse comportamento.  
  
 Deve ser combinada com a `DefaultInvisible` sinalizador.  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 NoShowOnMenuController  
 Se um comando que tenha esse sinalizador é posicionado em um controlador de menu, o comando não aparecerá na lista suspensa.  
  
 Válida para:`Button`  
  
 Para obter mais informações sobre sinalizadores de comando, consulte o [comando sinalizador elemento](../../extensibility/command-flag-element.md) documentação.  
  
##### <a name="general-requirements"></a>Requisitos gerais  
 O comando deve passar a seguinte série de testes antes de ser exibido e ativado:  
  
-   O comando é posicionado corretamente.  
  
-   O `DefaultInvisible` sinalizador não está definido.  
  
-   Barra de ferramentas ou menu pai está visível.  
  
-   O comando não é invisível devido a uma entrada de contexto no [VisibilityConstraints elemento](../../extensibility/visibilityconstraints-element.md) seção.  
  
-   Código de VSPackage que implementa o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interface Exibe e permite que o comando.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Nenhum código de interface interceptamos e agir sobre ele.  
  
-   Quando um usuário clica em seu comando, ele fica sujeito ao procedimento descrito em [roteamento algoritmo](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Comandos predefinidos de chamada  
 O [UsedCommands elemento](../../extensibility/usedcommands-element.md) permite que os VSPackages para acessar comandos que são fornecidos por outros VSPackages ou pelo IDE. Para fazer isso, crie um [UsedCommand elemento](../../extensibility/usedcommand-element.md) que tem o GUID e a ID do comando para usar. Isso garante que o comando será carregado pelo Visual Studio, mesmo se ele não é parte da configuração atual do Visual Studio. Para obter mais informações, consulte [UsedCommand elemento](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Aparência do elemento de interface  
 Considerações para selecionar e posicionar os elementos de comando são os seguintes:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferece muitos elementos de interface do usuário que aparecem de forma diferente dependendo de posicionamento.  
  
-   Um elemento de interface do usuário que é definido usando o `DefaultInvisible` sinalizador não será exibido no IDE, a menos que seja exibido por sua implementação de VSPackage de é o <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>método, ou associado a um determinado contexto de interface do usuário no `VisibilityConstraints` seção.</xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>  
  
-   Até mesmo um comando com êxito posicionado não pode ser exibido. Isso é porque o IDE automaticamente oculta ou exibe alguns comandos, dependendo de interfaces que o VSPackage (ou não) implementado. Por exemplo, a implementação do VSPackage de alguns criar interfaces de itens de menu relacionados à compilação de causas a serem mostradas automaticamente.  
  
-   Aplicando o `CommandWellOnly` sinalizador na definição de elemento de interface do usuário significa que o comando possa ser adicionado somente pela personalização.  
  
-   Comandos podem estar disponíveis apenas em determinados contextos de interface do usuário, por exemplo, somente quando uma caixa de diálogo é exibida quando o IDE está no modo de design.  
  
-   Para fazer com que determinados elementos de interface do usuário a ser exibido no IDE, você deve implementar uma ou mais interfaces ou escrever qualquer código.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo Menus e comandos](../../extensibility/extending-menus-and-commands.md)
