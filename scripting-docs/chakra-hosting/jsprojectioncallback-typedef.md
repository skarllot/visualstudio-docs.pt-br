---
title: Typedef JsProjectionCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 80d1c64f04f44a8560c25935fba2a48905a73260
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsprojectioncallback-typedef"></a>Typedef JsProjectionCallback
O retorno de chamada de JsRT que deve ser chamado com o contexto passado para `JsProjectionEnqueueCallback` no thread correto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `jsContext`  
 Requer uma chamada para `JsSetProjectionEnqueueCallback` para receber retornos de chamada.  
  
## <a name="remarks"></a>Comentários  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
