---
title: "Função JsGetRuntimeMemoryUsage | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetRuntimeMemoryUsage
helpviewer_keywords:
- JsGetRuntimeMemoryUsage function
ms.assetid: b9bd4146-bfbc-4cb1-a0e9-a0ded7fb09bd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 3519e4395ab5b3b7bbc5186c56775bdef9b12ecf
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetruntimememoryusage-function"></a>Função JsGetRuntimeMemoryUsage
Obtém o uso de memória atual para um tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetRuntimeMemoryUsage(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ size_t *memoryUsage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `runtime`  
 O tempo de execução cujo uso de memória deve ser recuperado.  
  
 `memoryUsage`  
 O uso de memória atual do tempo de execução, em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O uso de memória pode ser sempre recuperado, independentemente de o tempo de execução estar ou não ativo em outro thread.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
