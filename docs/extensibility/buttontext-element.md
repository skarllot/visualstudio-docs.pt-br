---
title: Elemento ButtonText | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 6
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
ms.openlocfilehash: babec1846979341ea4707eb2e4f0e1327bdc19d9
ms.lasthandoff: 02/22/2017

---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo permite que você especifique o texto que aparece em vários menus. Por padrão, o `ButtonText` elemento aparece em controladores de menu. O `ButtonText` elemento também se tornará o padrão se campos de texto em branco. O `ButtonText` elemento não pode ficar em branco, mesmo que os outros campos de texto são especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de cadeias de caracteres](../extensibility/strings-element.md)|Agrupa elementos de texto, como `ButtonText` e `CommandName`.|  
  
## <a name="text-value"></a>Valor de texto  
 O valor de texto de `ButtonText` elemento fornece o texto que é exibido para itens de menu, combinações e outros elementos de interface (UI) que têm texto visível.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
