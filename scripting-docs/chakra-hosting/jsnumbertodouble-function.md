---
title: "Função JsNumberToDouble | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsNumberToDouble
helpviewer_keywords:
- JsNumberToDouble function
ms.assetid: 5f52e8b6-2b70-49a3-879a-bd83ebf2ac33
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 3dba3205bcb55d3a9a233a5125a4854210b20f5d
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsnumbertodouble-function"></a>Função JsNumberToDouble
Recupera o valor de `double` de um valor numérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsNumberToDouble(  
   _In_ JsValueRef value,  
   _Out_ double *doubleValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 O valor numérico a converter em um valor `double`.  
  
 `doubleValue`  
 O valor `double`.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Essa função recupera o valor de um valor numérico. Ela falhará com `JsErrorInvalidArgument` se o tipo do valor não for numérico.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
