---
title: "Função JsConvertValueToBoolean | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsConvertValueToBoolean
helpviewer_keywords:
- JsConvertValueToBoolean function
ms.assetid: 7298ec72-a388-4334-b81b-1691ab4cecf0
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 10e2a5c91fe255e3eb9f3689e07fcfa149eb0d22
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsconvertvaluetoboolean-function"></a>Função JsConvertValueToBoolean
Converte o valor em booliano usando a semântica padrão de JavaScript.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsConvertValueToBoolean(  
   _In_ JsValueRef value,  
   _Out_ JsValueRef *booleanValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 O valor a ser convertido.  
  
 `booleanValue`  
 O valor convertido.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
