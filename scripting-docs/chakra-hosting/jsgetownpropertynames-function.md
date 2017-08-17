---
title: "Função JsGetOwnPropertyNames | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetOwnPropertyNames
helpviewer_keywords:
- JsGetOwnPropertyNames function
ms.assetid: 0c17ea06-b17f-4ea3-ad04-1259a4d1b6de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: f4efd4133fb2636afdacba205f7be1ba7980a36c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetownpropertynames-function"></a>Função JsGetOwnPropertyNames
Obtém a lista de todas as propriedades no objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetOwnPropertyNames(  
   _In_ JsValueRef object,  
   _Out_ JsValueRef *propertyNames  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto do qual obter os nomes de propriedade.  
  
 `propertyNames`  
 Uma matriz de nomes de propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
