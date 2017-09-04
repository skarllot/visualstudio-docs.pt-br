---
title: Typedef JsBeforeCollectCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58bece47-4e6d-49e7-a93d-b6a8f9928b41
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 50e2b79ceb2809aee0348bae594e8494596b6089
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsbeforecollectcallback-typedef"></a>Typedef JsBeforeCollectCallback
Um retorno de chamada chamado antes da coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void (CALLBACK *JsBeforeCollectCallback)(  
_In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 callbackState  
 O estado passou para JsSetBeforeCollectCallback.  
  
## <a name="remarks"></a>Comentários  
 Use JsSetBeforeCollectCallback para registrar este retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
