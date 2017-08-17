---
title: "Função JsHasException | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsHasException
helpviewer_keywords:
- JsHasException function
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 32334f4b8787bebaffb9553fcdd40f85334462cb
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jshasexception-function"></a>Função JsHasException
Determina se o tempo de execução do contexto atual está em um estado de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hasException`  
 Se o tempo de execução do contexto atual está ou não no estado de exceção.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Se uma chamada para o tempo de execução resulta em uma exceção (como o resultado da execução de um script ou então devido a algo como uma falha de conversão), o tempo de execução é colocado em um "estado de exceção". Todas as chamadas para qualquer contexto criado pelo tempo de execução (exceto as APIs de exceção) falharão com `JsErrorInExceptionState` até que a exceção seja apagada.  
  
 Se o tempo de execução do contexto atual estiver no estado de exceção quando um retorno de chamada retornar para o mecanismo, o mecanismo relançará a exceção automaticamente.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
