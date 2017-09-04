---
title: "Função JsSetRuntimeMemoryAllocationCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryAllocationCallback
helpviewer_keywords:
- JsSetRuntimeMemoryAllocationCallback function
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 755ab36c8edb8c0350eb2b245e060344c8825dee
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetruntimememoryallocationcallback-function"></a>Função JsSetRuntimeMemoryAllocationCallback
Define um retorno de chamada de alocação de memória para o tempo de execução especificado  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `runtime`  
 O tempo de execução para o qual registrar o retorno de chamada de alocação.  
  
 `callbackState`  
 Estado fornecido pelo usuário que será passado de volta para o retorno de chamada.  
  
 `allocationCallback`  
 Retorno de alocação de memória a ser chamado para eventos de alocação de memória.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Registrar um retorno de chamada de alocação de memória fará com que o tempo de execução retorne chamada para o host sempre que ele adquirir memória de ou liberar memória para o sistema operacional. A rotina de retorno de chamada é chamada antes de o gerenciador de memória de tempo de execução alocar um bloco de memória. A alocação será rejeitada se o retorno de chamada retornar false. O gerenciador de memória de tempo de execução também invocará a rotina de retorno de chamada depois de liberar um bloco de memória, bem como após falhas de alocação.  
  
 O retorno de chamada é invocado no thread de execução de tempo de execução atual, portanto, a execução é bloqueada até que o retorno de chamada seja concluído.  
  
 O valor retornado do retorno de chamada não é armazenado; alocações anteriormente rejeitadas não impedirão que o tempo de execução invoque o retorno de chamada novamente mais tarde para novas alocações de memória.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
