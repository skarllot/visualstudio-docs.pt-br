---
title: Typedef JsObjectBeforeCollectCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f21a064a-579f-44cb-9d21-76b62e8c18f5
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 7d11de01c44792d3e41cc2721a404f2ed906f02e
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsobjectbeforecollectcallback-typedef"></a>Typedef JsObjectBeforeCollectCallback
Um retorno de chamada chamado antes de coletar um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void (CALLBACK *JsObjectBeforeCollectCallback)(  
  _In_ JsRef ref,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ref`  
 O objeto a ser coletado.  
  
 `callbackState`  
 O estado passado para `JsSetObjectBeforeCollectCallback`.  
  
## <a name="remarks"></a>Comentários  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
