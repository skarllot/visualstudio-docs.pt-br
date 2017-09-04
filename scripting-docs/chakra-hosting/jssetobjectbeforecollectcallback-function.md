---
title: "Função JsSetObjectBeforeCollectCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6a472e63afd909ee7bcb74cb2fdd1ae98d6a2938
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetobjectbeforecollectcallback-function"></a>Função JsSetObjectBeforeCollectCallback
Define uma função de retorno de chamada que é chamada pelo tempo de execução antes da coleta de lixo de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ref`  
 O objeto para o qual registrar o retorno de chamada.  
  
 `callbackState`  
 Estado fornecido pelo usuário que será passado de volta para o retorno de chamada.  
  
 `objectBeforeCollectCallback`  
 A função de retorno de chamada que está sendo definida. Use null para limpar o retorno de chamada registrado anteriormente.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada é invocado no thread de execução de tempo de execução atual, portanto, a execução é bloqueada até que o retorno de chamada seja concluído.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
