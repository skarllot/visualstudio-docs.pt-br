---
title: Elemento pai | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
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
ms.openlocfilehash: 0da0bd0aceaccdbf8d2cf11fd3490a3e5810ad2e
ms.lasthandoff: 02/22/2017

---
# <a name="parent-element"></a>Elementos pai
O pai de um botão ou caixa de combinação só pode ser um grupo. O pai de um menu ou grupo pode ser qualquer menu ou grupo. Em um [CommandPlacement elemento](../extensibility/commandplacement-element.md), esse elemento é necessário; em todas as outras instâncias é opcional. Se este elemento for omitido, o pai do `Group_Undefined:0` será implícita.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. Identificador do comando GUID do GUID/ID.|  
|id|Necessário. Identificador do comando de ID do GUID/ID.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que fornece um VSPackage para o ambiente de desenvolvimento integrado (IDE). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|  
|[Elemento de botões](../extensibility/buttons-element.md)|Grupos de [elemento Button](../extensibility/button-element.md) elementos.|  
|[Elemento de menus](../extensibility/menus-element.md)|Define todos os menus que implementa um VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando de um VSPackage.|  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
