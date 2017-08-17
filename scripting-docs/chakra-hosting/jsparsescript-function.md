---
title: "Função JsParseScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsParseScript
helpviewer_keywords:
- JsParseScript function
ms.assetid: e9d0e363-7cbe-43eb-9dc0-1f47e586c9ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: de55c249b6fb5b723086f48312904f0232f0a11b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsparsescript-function"></a>Função JsParseScript
Analisa um script e retorna uma função representando o script.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsParseScript(  
   _In_z_ const wchar_t *script,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `script`  
 O script a ser analisado.  
  
 `sourceContext`  
 Um cookie identificando o script que pode ser usado por contextos de script depuráveis.  
  
 `sourceUrl`  
 O local de onde o script veio.  
  
 `result`  
 Uma função representando o código do script.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
