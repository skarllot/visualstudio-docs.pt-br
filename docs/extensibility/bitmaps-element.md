---
title: Elemento de bitmaps | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
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
ms.openlocfilehash: 79d98cc0779e5c90d27f8c7b50e4e5dc169feef7
ms.lasthandoff: 02/22/2017

---
# <a name="bitmaps-element"></a>Elemento de bitmaps
Grupos de [Bitmap elemento](../extensibility/bitmap-element.md) elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de bitmaps](../extensibility/bitmaps-element.md)|Agrupa elementos do Bitmap.|  
|[Elemento de bitmap](../extensibility/bitmap-element.md)|Define um bitmap.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Representa a coleção de comandos na barra de ferramentas VSPackage.|  
  
## <a name="example"></a>Exemplo  
  
```  
<Bitmaps>  
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
    usedList="1, 2, 3, 4"/>  
</Bitmaps>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como os VSPackages adicionar elementos de Interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Barras de ferramentas, Menus e comandos](../extensibility/internals/commands-menus-and-toolbars.md)
