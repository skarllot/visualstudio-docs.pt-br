---
title: "Função JsSetRuntimeBeforeCollectCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeBeforeCollectCallback
helpviewer_keywords:
- JsSetRuntimeBeforeCollectCallback function
ms.assetid: 7b2fb911-6007-4ed9-a307-66cefe590ea4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 469b33a324f67d17bd6f5156da7cce169b98c663
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetruntimebeforecollectcallback-function"></a>Função JsSetRuntimeBeforeCollectCallback
Define uma função de retorno de chamada que é chamada pelo tempo de execução antes da coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeBeforeCollectCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsBeforeCollectCallback beforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `runtime`  
 O tempo de execução para o qual registrar o retorno de chamada de alocação.  
  
 `callbackState`  
 Estado fornecido pelo usuário que será passado de volta para o retorno de chamada.  
  
 `beforeCollectCallback`  
 A função de retorno de chamada que está sendo definida.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada é invocado no thread de execução de tempo de execução atual, portanto, a execução é bloqueada até que o retorno de chamada seja concluído.  
  
 O retorno de chamada pode ser usado por hosts para se preparar para a coleta de lixo. Por exemplo, liberando referências desnecessárias em objetos Chakra.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
