---
title: EndTrackingContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a376142b5765967cf666d5e33cfc8327d00c229e
ms.lasthandoff: 02/22/2017

---
# <a name="endtrackingcontext"></a>EndTrackingContext
Finaliza o contexto atual de acompanhamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o conjunto de bits [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) se o contexto de acompanhamento tiver sido finalizado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
