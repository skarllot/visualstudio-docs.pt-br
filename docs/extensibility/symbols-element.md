---
title: "Símbolos de elemento | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
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
ms.openlocfilehash: 9376a397c5573a759205288d04c4628d0169c66e
ms.lasthandoff: 02/22/2017

---
# <a name="symbols-element"></a>Elemento de símbolos
Define os GUIDs e IDs que são usadas por outros elementos VSCT. Para código não gerenciado, essas informações geralmente é causado por arquivos de cabeçalho especificados por [Extern elemento](../extensibility/extern-element.md). Código gerenciado usa os elementos filho do elemento símbolos para definir essas informações.  
  
 Se você criar um arquivo. VSCT de um arquivo de .cto existente, os símbolos serão gerados como filhos do elemento de símbolos. Para obter mais informações, consulte [como: criar um. Arquivo VSCT de uma já existente. Arquivo CTO](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 O elemento de símbolos não deve ser confundido com o [definir elemento](../extensibility/define-element.md), que define os pares de nome-valor para uso pelo pré-processador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Nenhum||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|GuidSymbol|Define um símbolo GUID. GuidSymbol possui dois atributos obrigatórios: nome e valor. O nome é o nome do símbolo e o valor é o valor do GUID como uma cadeia de caracteres.<br /><br /> Por exemplo:\<GuidSymbol nome = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|IDSymbol|Define um símbolo. IDSymbol possui dois atributos obrigatórios: nome e valor. O nome é o nome do símbolo e o valor é o valor do símbolo como uma cadeia de caracteres.<br /><br /> Por exemplo:\<IDSymbol nome = "MyMenuGroup" value = "0x1020" / >|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|O elemento raiz do arquivo. VSCT.|  
  
## <a name="example"></a>Exemplo  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
