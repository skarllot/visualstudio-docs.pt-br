---
title: Elemento GuidSymbol | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
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
ms.openlocfilehash: c2d90c629974136b3c988a1ba0cb7701f62f45ad
ms.lasthandoff: 02/22/2017

---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
O `GuidSymbol` elemento contém o GUID do par GUID:ID que representa um menu, o grupo ou o comando. A ID vem de um `IDSymbol` elemento o `GuidSymbol` elemento. O `GuidSymbol` elemento tem um `name` que fornece um nome amigável para o GUID, que está contido no atributo de `value` atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Necessário. Nome do símbolo GUID.|  
|Valor |Necessário. GUID do símbolo GUID.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contém a ID do par GUID:ID que representa um menu, o grupo ou o comando.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de símbolos](../extensibility/symbols-element.md)|Grupos de `GuidSymbol` elementos em um arquivo. VSCT.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um arquivo. VSCT contém três `GuidSymbol` elementos no seu `Symbols` seção, uma para o pacote em si, uma para o conjunto de comandos (a coleção de menus, grupos e comandos que disponibiliza o pacote) e outra para os bitmaps que fornecer ícones de botões e outros componentes visuais. Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter um único `value`. No entanto, `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que eles têm diferentes pais.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
