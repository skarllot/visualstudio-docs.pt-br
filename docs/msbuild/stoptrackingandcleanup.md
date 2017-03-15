---
title: StopTrackingAndCleanup | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
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
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: a0093df3ec1ba5b7501074177f91cc6c47574220
ms.lasthandoff: 02/22/2017

---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Interrompe o acompanhamento e libera a memória usada pela sessão de acompanhamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o conjunto de bits [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) se o acompanhamento tiver sido interrompido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
