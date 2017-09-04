---
title: "Função JsRunSerializedScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsRunSerializedScript
helpviewer_keywords:
- JsRunSerializedScript function
ms.assetid: 3fd3f6f1-eb3e-4751-92a5-c93b1035f3b2
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: b770edbcaa4e7dc36f295407627c10a8b574b88b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsrunserializedscript-function"></a>Função JsRunSerializedScript
Executa um script serializado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScript(  
   _In_z_ const wchar_t *script,  
   _In_ BYTE *buffer,  
   _In_ JsSourceContext sourceContext,  
   _In_z_ const wchar_t *sourceUrl,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `script`  
 O código-fonte do script serializado.  
  
 `buffer`  
 O script serializado.  
  
 `sourceContext`  
 Um cookie identificando o script que pode ser usado por contextos de script depuráveis.  
  
 `sourceUrl`  
 O local de onde o script veio.  
  
 `result`  
 O resultado da execução do script, se houver. Este parâmetro pode ser nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 O buffer não é persistido na memória pelo mecanismo de script, de modo que o código deve mantê-lo vivo enquanto puder ser usado para executar scripts.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
