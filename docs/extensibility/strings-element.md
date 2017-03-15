---
title: Elemento de cadeias de caracteres | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
caps.latest.revision: 9
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
ms.openlocfilehash: 86e0148d495914b1cb1c0f0d19125992930a9521
ms.lasthandoff: 02/22/2017

---
# <a name="strings-element"></a>Elemento de cadeias de caracteres
O elemento de cadeias de caracteres deve conter pelo menos um **ButtonText** elemento filho. Todos os outros elementos filho são opcionais. XML inválido, como caracteres '< /' e '<’ must="" be="" coded="" as="" entities=""></’>&amp;'e'&lt;' e assim por diante).  
  
 Um e comercial na cadeia de texto Especifica o atalho de teclado para o comando.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|linguagem|Opcional. Language = ".".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|ButtonText|Esse campo e cinco seguintes campos de texto em uma definição de comando permitem especificar o texto que aparece em vários menus. Por padrão, o `ButtonText` campo aparece em controladores de menu. O `ButtonText` campo também se tornará o padrão se campos de texto em branco. O `ButtonText` campo não pode ficar em branco, mesmo se os outros campos de texto são especificados.|  
|ToolTipText|O `ToolTipText` campo especifica o texto que aparece na dica de ferramenta para um item de menu.<br /><br /> Se o `ToolTipText` campo estiver em branco, o `ButtonText` campo será usado.|  
|MenuText|O `MenuText` campo especifica o texto que é exibido para um comando se ele estiver no menu principal, uma barra de ferramentas em um menu de atalho ou em um submenu. Se o `MenuText` campo estiver em branco, o ambiente de desenvolvimento integrado (IDE) usa o `ButtonText` campo. O `MenuText` campo também pode ser usado para localização.<br /><br /> Para menus de atalho, o `MenuText` campo é o nome que é exibido na barra de Menus de atalho, que permite a personalização de menus de atalho no IDE. Portanto, ser específico no qual o nome seu menu de atalho; Por exemplo, use "Menu de atalho do Widget pacote" em vez de "Atalho".<br /><br /> Se o `MenuText` campo não for especificado, o `ButtonText` campo será usado.|  
|CommandName|O `CommandName` campo especifica o texto que aparece na categoria de teclado no **comandos** guia o **personalizar** caixa de diálogo (disponível ao clicar em **personalizar** no **ferramentas** menu).|  
|CanonicalName|O inglês `CanonicalName` campo especifica o nome do comando no texto em inglês que pode ser inserido no **comando** janela para executar o item de menu. O IDE remove quaisquer caracteres que não são letras, dígitos, sublinhados ou pontos inseridos. Esse texto é concatenado, em seguida, o `ButtonText` campo para definir o comando. Por exemplo, **novo projeto** sobre o **arquivo** menu torna-se o comando, File.NewProject.<br /><br /> Se o inglês `CanonicalName` campo não for especificado, o IDE usa o `ButtonText` campo e faixas todos exceto letras, dígitos, sublinhados e pontos inseridos. Por exemplo, o texto do botão "< / definir comandos..." se torna DefineCommands, onde o e comercial, o espaço e o botão de reticências são removidos.<br /><br /> Se o `TextChanges` sinalizador for especificado e o texto do comando é alterado, o comando correspondente reconhecido pelo **comando** janela não altera; ele permanece a forma canônica do original `ButtonText` ou inglês `CanonicalName` campos.|  
|LocCanonicalName|O `LocCanonicalName` campo se comporta de forma idêntica para o inglês `CanonicalName` campo mas permite que o texto de comando localizada seja especificada. Os dois campos canônicos podem ser especificados. Como o IDE analisa apenas texto inserido no **comando** janela e associa-o com um comando, inglês e outro idioma texto pode ser associado com o mesmo comando.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de botão](../extensibility/button-element.md)|Define um elemento que o usuário pode interagir com.|  
|[Elemento de menu](../extensibility/menu-element.md)|Define um item único de menu.|  
|[Elemento de combinação](../extensibility/combo-element.md)|Define os comandos que aparecem em uma caixa de combinação.|  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
