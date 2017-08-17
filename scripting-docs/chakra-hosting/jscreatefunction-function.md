---
title: "Função JsCreateFunction | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsCreateFunction
helpviewer_keywords:
- JsCreateFunction function
ms.assetid: b298a96a-5ef7-4203-a8c8-55f9bfc6d2bb
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 4fa0b39c0475814b036784a9dbb48553d50a83ea
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreatefunction-function"></a>Função JsCreateFunction
Cria uma nova função JavaScript.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsCreateFunction(  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nativeFunction`  
 O método a ser chamado quando a função é invocada.  
  
 `callbackState`  
 Estado fornecido pelo usuário que será passado de volta para o retorno de chamada.  
  
 `function`  
 O novo objeto de função.  
  
## <a name="return-value"></a>Valor de retorno  
 O resultado da chamada, se houver alguma.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
