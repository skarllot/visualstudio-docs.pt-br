---
title: Elemento de sinalizador de comando | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
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
ms.openlocfilehash: 487d6507191ec89f35d92b113d4951dfa7c36315
ms.lasthandoff: 02/22/2017

---
# <a name="command-flag-element"></a>Elemento de sinalizador de comando
Modifica seu elemento pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 A seção a seguir descreve os valores de elemento válido.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Valor|Descrição|  
|-----------|-----------------|  
|AllowParams|Indica que os usuários podem inserir parâmetros de comando na **comando** janela quando eles digitarem o nome canônico do comando.<br /><br /> Válida para:`Button`|  
|AlwaysCreate|Menu será criado mesmo que ele não tem grupos ou botões.<br /><br /> Válida para:`Menu`|  
|CaseSensitive|Entradas de usuário diferenciam maiusculas de minúsculas.<br /><br /> Válida para:`Combo`|  
|CommandWellOnly|Aplica esse sinalizador se o comando não aparecer no menu de nível superior e quiser torná-lo disponível para personalização do shell adicionais, por exemplo, para associá-lo a um atalho de teclado. Depois que o VSPackage é instalado, você pode personalizar esses comandos abrindo o **opções** caixa de diálogo e, em seguida, editando o posicionamento de comando na **teclado ambiente** categoria. Esse sinalizador não afeta o posicionamento em menus de atalho, barras de ferramentas, controladores de menu ou submenus.<br /><br /> Válido para: `Button`,`Combo`|  
|DefaultDisabled|Por padrão, o comando será desabilitado se o VSPackage que implementa não está carregado ou `QueryStatus` método não foi chamado.<br /><br /> Válido para: `Button`,`Combo`|  
|DefaultDocked|Encaixado por padrão. Essa configuração não se aplica a barras de ferramentas, porque elas sempre são encaixadas.|  
|DefaultInvisible|Por padrão, o comando é invisível se o VSPackage que implementa não está carregado ou `QueryStatus` método não foi chamado.<br /><br /> Recomendamos que você combine isso com o `DynamicVisibility` sinalizador.<br /><br /> Valid for: `Button`, `Combo`,`Menu`|  
|DontCache|O ambiente de desenvolvimento não armazena em cache o `QueryStatus` resultados do método para este comando.<br /><br /> Para um menu, isso indica que um controlador de menu não armazenar em cache o texto de seus itens de menu. Use esse sinalizador quando o menu contém itens dinâmicos ou itens que têm texto dinâmico.<br /><br /> Válido para: `Button`,`Menu`|  
|DynamicItemStart|Indica o início de uma lista dinâmica. Isso permite que o ambiente criar uma lista sucessivamente chamando o `QueryStatus` método em itens de lista até que o sinalizador OLECMDERR_E_UNSUPPORTED é retornado. Isso funciona bem para itens como usados mais recentemente (MRU) listas e listas de janela.<br /><br /> Válida para:`Button`|  
|DynamicVisibility|A visibilidade do comando pode ser alterada por meio de `QueryStatus` método ou por meio de um GUID que está incluído no contexto de `VisibilityConstraints` seção.<br /><br /> Aplica-se aos comandos que aparecem nos menus e barras de ferramentas de janela de ferramenta, mas não em barras de ferramentas de nível superior que aparecem na janela principal. Itens de nível superior da barra de ferramentas podem ser desabilitadas, mas não ocultas, quando o sinalizador OLECMDF_INVISIBLE é retornado do `QueryStatus` método. Comandos da barra de ferramentas que aparecem nas barras de ferramentas de janela de ferramenta podem ser oculto.<br /><br /> Em um menu, esse sinalizador indica também que ele deve ser automaticamente ocultado quando todos os seus membros estão ocultos. Esse sinalizador é geralmente atribuído aos submenus, como menus de nível superior já têm esse comportamento.<br /><br /> Esse sinalizador deve ser combinado com o `DefaultInvisible` sinalizador.<br /><br /> Valid for: `Button`, `Combo`,`Menu`|  
|Teclas de filtragem|Consulte o tópico de filtragem de chaves em [combinação elemento](../extensibility/combo-element.md).<br /><br /> Válida para:`Combo`|  
|FixMenuController|Se esse comando é posicionado em um controlador de menu, o comando é sempre o padrão; ou seja, o comando é selecionado sempre que o próprio botão de controlador de menu é selecionado. Se o controlador de menu tem o `TextIsAnchorCommand` , em seguida, o controlador de menu também usa o texto do comando que tem o sinalizador será definido, o `FixMenuController` sinalizador.<br /><br /> Somente um comando em um controlador de menu deve ter o `FixMenuController` sinalizador. Se mais de um comando é marcado assim, o último comando no menu torna-se o comando padrão.<br /><br /> Válida para:`Button`|  
|IconAndText|Mostra um ícone e texto no menu e barra de ferramentas.<br /><br /> Valid for: `Button`, `Combo`,`Menu`|  
|NoAutoComplete|Recurso Preenchimento automático é desabilitado.<br /><br /> Válida para:`Combo`|  
|NoButtonCustomize|Não permitir que o usuário personalize esse botão.<br /><br /> Válido para: `Button`,`Combo`|  
|NoKeyCustomize|Não habilite a personalização do teclado.<br /><br /> Válido para: `Button`,`Combo`|  
|NoShowOnMenuController|Se esse comando é posicionado em um controlador de menu, o comando não aparecerá na lista suspensa.<br /><br /> Válida para:`Button`|  
|NotInTBList|Não aparece na lista de barras de ferramentas disponíveis. Isso é válido somente para tipos de menu da barra de ferramentas.<br /><br /> Válida para:`Menu`|  
|NoToolbarClose|Usuário não é possível fechar a barra de ferramentas. Isso é válido somente para tipos de menu da barra de ferramentas.<br /><br /> Válida para:`Menu`|  
|PICT|Mostra apenas um ícone em uma barra de ferramentas, mas somente texto em um menu. Se nenhum ícone for especificado, mostra um espaço em branco que pode ser clicado em uma barra de ferramentas.<br /><br /> Válida para:`Button`|  
|PostExec|Faz com que o comando sem bloqueio. O ambiente de desenvolvimento adia a execução até que todas as consultas de pré-processamento são concluídas.<br /><br /> Válida para:`Button`|  
|RouteToDocs|O comando é roteado para o documento ativo.<br /><br /> Válida para:`Button`|  
|StretchHorizontally|Quando esse sinalizador estiver definido, a largura torna-se a largura mínima da caixa de combinação e, se houver espaço na barra de ferramentas, caixa de combinação expande para preencher o espaço disponível. Isso ocorre apenas se a barra de ferramentas está ancorada horizontalmente e apenas uma caixa de combinação na barra de ferramentas pode usar o sinalizador (o sinalizador é ignorado em todos, exceto a primeira caixa de combinação).<br /><br /> Válida para:`Combo`|  
|TextMenuUseButton|Use o `ButtonText` campo menus. O campo padrão é `MenuText` se for especificado.<br /><br /> Válida para:`Button`|  
|TextoAltera|O texto de comando ou menu pode ser alterado em tempo de execução, normalmente por meio de `QueryStatus` método.<br /><br /> Válido para: `Button`,`Menu`|  
|TextChangesButton|Válida para:`Button`|  
|TextIsAnchorCommand|Para um controlador de menu, o texto do menu é extraído do comando padrão (âncora). Um comando de âncora é o último comando selecionado ou travada. Se este sinalizador não for definido, o controlador de menu usa seu próprio `MenuText` campo. No entanto, clique em controlador de menu ainda permite que o último comando selecionado desse controlador.<br /><br /> Recomendamos que você combine esse sinalizador com a `TextChanges` sinalizador.<br /><br /> Esse sinalizador se aplica apenas aos menus do tipo MenuController ou MenuControllerLatched.<br /><br /> Válida para:`Menu`|  
|TextMenuCtrlUseMenu|Use o `MenuText` campo nos controladores de menu. O campo padrão é `ButtonText`.<br /><br /> Válida para:`Button`|  
|TextMenuUseButton|Use o `ButtonText` campo menus. O campo padrão é `MenuText` se for especificado.<br /><br /> Válida para:`Button`|  
|TextOnly|Mostra apenas o texto em uma barra de ferramentas ou um menu, mas nenhum ícone mesmo se o ícone for especificado.<br /><br /> Válida para:`Button`|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de botões](../extensibility/buttons-element.md)|Fornece um grupo de [elemento Button](../extensibility/button-element.md) elementos.|  
|[Elemento de menus](../extensibility/menus-element.md)|Define todos os menus que implementa um VSPackage.|  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
