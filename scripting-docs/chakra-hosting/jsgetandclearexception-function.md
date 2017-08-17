---
title: "Função JsGetAndClearException | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetAndClearException
helpviewer_keywords:
- JsGetAndClearException function
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 3e7e4f89bac59aa776762586ab20fa831b5c24bf
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetandclearexception-function"></a>Função JsGetAndClearException
Retorna a exceção que fez com que o tempo de execução do contexto atual estivesse no estado de exceção e redefine o estado de exceção para esse tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `exception`  
 A exceção para o tempo de execução do contexto atual.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Se o tempo de execução do contexto atual não está em um estado de exceção, essa API retorna `JsErrorInvalidArgument`. Se o tempo de execução estiver desabilitado, isso retornará uma exceção indicando que o script foi encerrado, mas ele não limpará a exceção (a exceção será limpa se o tempo de execução for reabilitado usando `JsEnableRuntimeExecution`).  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
