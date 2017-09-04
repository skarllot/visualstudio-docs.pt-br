---
title: "Função JsSetPromiseContinuationCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6ef0faf4-1500-4bd9-aeca-c208492af8ea
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: c20b5c81bd34a44158a975f0c1aed88614e01022
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetpromisecontinuationcallback-function"></a>Função JsSetPromiseContinuationCallback
Define uma função de retorno de chamada de continuação de promessa que é chamada pelo contexto quando uma tarefa precisa ser colocada na fila para execução futura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetPromiseContinuationCallback(  
   _In_ JsPromiseContinuationCallback promiseContinuationCallback,  
   _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `promiseContinuationCallback`  
 A função de retorno de chamada que está sendo definida.  
  
 `callbackState`  
 Estado fornecido pelo usuário que será passado de volta para o retorno de chamada.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
