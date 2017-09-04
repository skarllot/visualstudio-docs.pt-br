---
title: Typedef JsProjectionCallbackContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsprojectioncallbackcontext-typedef"></a>Typedef JsProjectionCallbackContext
O contexto passado do JsRT para o retorno de chamada de aplicativo, JsProjectionEnqueueCallback e, em seguida, passado de volta para JsRT no retorno de chamada fornecido, `JsProjectionCallback`, pelo aplicativo no thread correto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>Comentários  
 Requer uma chamada para `JsSetProjectionEnqueueCallback` para receber retornos de chamada.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
