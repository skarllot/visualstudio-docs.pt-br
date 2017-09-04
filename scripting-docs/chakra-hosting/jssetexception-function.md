---
title: "Função JsSetException | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetException
helpviewer_keywords:
- JsSetException function
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 5d8fce71f14dedea02e1809fb72281f575f60604
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetexception-function"></a>Função JsSetException
Define o tempo de execução do contexto atual para um estado de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `exception`  
 A exceção de JavaScript a definir para o tempo de execução do contexto atual.  
  
## <a name="return-value"></a>Valor de retorno  
 `JsNoError` se o mecanismo foi definido em um estado de exceção; caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Se o tempo de execução do contexto atual já está em um estado de exceção, essa API retorna `JsErrorInExceptionState`.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
