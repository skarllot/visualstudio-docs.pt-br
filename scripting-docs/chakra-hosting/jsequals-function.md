---
title: "Função JsEquals | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsEquals
helpviewer_keywords:
- JsEquals function
ms.assetid: 8377a7b6-12ff-43e4-8cc8-5a5a198a168b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 4bb0a40cf74021fbad081745ef27c79a6a4b2b78
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsequals-function"></a>Função JsEquals
Compare dois valores de JavaScript para igualdade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsEquals(  
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
 Se os valores são iguais ou não.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Essa função é equivalente ao operador `==` em JavaScript.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
