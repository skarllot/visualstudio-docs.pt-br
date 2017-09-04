---
title: "Função JsGetStringLength | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetStringLength
helpviewer_keywords:
- JsGetStringLength function
ms.assetid: e9f9f28c-e644-439c-aee5-7ce362f71347
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 1db3253d3889da81a14bc41fe06fd16f4e90b81c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetstringlength-function"></a>Função JsGetStringLength
Obtém o comprimento de um valor de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetStringLength(  
   _In_ JsValueRef stringValue,  
   _Out_ int *length  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stringValue`  
 O valor de cadeia de caracteres cujo comprimento obter.  
  
 `length`  
 O comprimento da cadeia de caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
