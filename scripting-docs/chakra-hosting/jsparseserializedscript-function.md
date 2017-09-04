---
title: "Função JsParseSerializedScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsParseSerializedScript
helpviewer_keywords:
- JsParseSerializedScript function
ms.assetid: 40d0c7c4-fd5b-46ed-9e65-38c2db2fc859
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 7eb18c8537d7bdfe69969293b66a5909ba7c3fa1
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsparseserializedscript-function"></a>Função JsParseSerializedScript
Analisa um script serializado e retorna uma função representando o script.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsParseSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `script`  
 O script a ser analisado.  
  
 `buffer`  
 O script serializado.  
  
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
  
 O buffer não é persistido na memória pelo mecanismo de script, de modo que o código deve mantê-lo vivo enquanto puder ser usado para executar scripts.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
