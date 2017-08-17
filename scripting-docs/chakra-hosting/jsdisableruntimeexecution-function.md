---
title: "Função JsDisableRuntimeExecution | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsDisableRuntimeExecution
helpviewer_keywords:
- JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsdisableruntimeexecution-function"></a>Função JsDisableRuntimeExecution
Suspende a execução do script e encerra quaisquer scripts em execução em um tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `runtime`  
 O tempo de execução a ser suspenso.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Chamadas para um tempo de execução suspenso falharão até que `JsEnableRuntimeExecution` seja chamado.  
  
 Esta API não precisa ser chamada no thread no qual o tempo de execução está ativo. Embora o tempo de execução será colocado em um estado suspenso, um script em execução pode não ser suspenso imediatamente; um script em execução será encerrado com uma exceção não capturável assim que possível.  
  
 Suspender a execução em um tempo de execução já suspenso não é operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
