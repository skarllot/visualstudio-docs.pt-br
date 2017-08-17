---
title: "Função JsGetGlobalObject | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetGlobalObject
helpviewer_keywords:
- JsGetGlobalObject function
ms.assetid: d3e91e64-1ca3-4d2b-aada-725ded0fd0b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 10ee0277098e29abd44c360be4dcd5b246c1b04d
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetglobalobject-function"></a>Função JsGetGlobalObject
Obtém o objeto global no contexto de script atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetGlobalObject(  
   _Out_ JsValueRef *globalObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `globalObject`  
 O objeto global.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
