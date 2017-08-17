---
title: Typedef JsMemoryAllocationCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 511babc7-3caa-4ee5-82a2-943bbd34db8d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 9672c23f48a2cb3e20de58012b267b30f4514d66
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsmemoryallocationcallback-typedef"></a>Typedef JsMemoryAllocationCallback
Rotina de retorno de chamada implementada pelo usuário para eventos de alocação de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef bool (CALLBACK * JsMemoryAllocationCallback)(  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryEventType allocationEvent,  
   _In_ size_t allocationSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 callbackState  
 O estado passou para JsSetRuntimeMemoryAllocationCallback.  
  
 allocationEvent  
 O tipo de evento de alocação de tipo.  
  
 allocationSize  
 O tamanho da alocação.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Quando o evento JsMemoryAllocate retorna true, o tempo de execução continua com alocação. Quando retorna false, indica que o pedido de alocação foi rejeitado. O valor retornado é ignorado para outros eventos de alocação.  
  
## <a name="remarks"></a>Comentários  
 Use JsSetRuntimeMemoryAllocationCallback para registrar este retorno de chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
