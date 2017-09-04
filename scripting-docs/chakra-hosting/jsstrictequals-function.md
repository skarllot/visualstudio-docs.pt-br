---
title: "Função JsStrictEquals | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStrictEquals
helpviewer_keywords:
- JsStrictEquals function
ms.assetid: b35bc655-7ff8-496a-b678-8950bb976047
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 3d5d88bc98db3d0ec7fa8e80fd72a287ef8957e8
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsstrictequals-function"></a>Função JsStrictEquals
Compare dois valores de JavaScript para igualdade estrita.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsStrictEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object1`  
 O primeiro objeto a ser comparado.  
  
 `object2`  
 O segundo objeto a ser comparado.  
  
 `result`  
 Se os valores são estritamente iguais ou não.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Essa função é equivalente ao operador `===` em JavaScript.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
