---
title: Elemento de bitmap | Documentos do Microsoft
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
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
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
ms.openlocfilehash: c7d3cffeb7d31cab6fd05e5df5cabd89bfb0482b
ms.lasthandoff: 02/22/2017

---
# <a name="bitmap-element"></a>Elemento de bitmap
Define um bitmap. O bitmap é carregado de um recurso ou de um arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. GUID do identificador do comando GUID/ID.<br /><br /> O atributo guid para um bitmap não está associado com qualquer VSPackage ou outro grupo de comando.  Ele deve ser exclusivo para a definição de bitmap e não deve ser usado para qualquer outra finalidade.|  
|resID|ID do identificador do comando GUID/ID. O resID ou o atributo href é necessário.<br /><br /> O atributo resID é uma ID de recurso inteiro que determina a faixa de bitmap que deve ser carregada durante a mesclagem de tabela de comando.  Quando a tabela de comando está sendo carregada, os bitmaps especificados pelo identificador do recurso serão carregados do recurso do mesmo módulo.|  
|usedList|Necessário se o atributo resID estiver presente. Seleciona as imagens disponíveis na faixa de bitmap.|  
|href|Caminho para o bitmap. O resID ou o atributo href é necessário.<br /><br /> Caminho de inclusão é pesquisado para o arquivo de imagem indicado, que é inserido no binário resultante.  Durante a mesclagem de tabela do comando, a imagem é copiada e nenhum recurso adicional de pesquisa ou carga é necessária.  Se o atributo usedList não estiver presente, todas as imagens na faixa de estão disponíveis. **Observação:** imagens podem ser fornecidas em vários formatos que incluem. bmp,. PNG e. gif.  Versões anteriores do compilador não oferecia suporte a imagens de bitmap de 32 bits que tiveram informações alfabéticos para transparência parcial. A solução alternativa para essas versões é usar o formato. PNG.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento de bitmaps](../extensibility/bitmaps-element.md)|Agrupa elementos do Bitmap.|  
  
## <a name="example"></a>Exemplo  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
