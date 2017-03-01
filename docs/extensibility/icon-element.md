---
title: "Elemento de ícone | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
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
ms.openlocfilehash: 98d930a74b964743f2a77a0943b7b3c773c0feda
ms.lasthandoff: 02/22/2017

---
# <a name="icon-element"></a>Elemento de ícone
O atributo guid da marca do ícone é o guid de um bitmap definido.  O atributo id seleciona o slot na faixa de bitmap. Esse elemento é opcional.  Se este elemento for omitido o valor de **guidOfficeIcon:msotcidNoIcon** será implícita.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. O guid de um bitmap definido.|  
|id|Necessário. Seleciona o slot na faixa de bitmap.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Nenhum.|Nenhum.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de botões](../extensibility/buttons-element.md)||  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
