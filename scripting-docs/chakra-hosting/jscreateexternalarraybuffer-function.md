---
title: "Função JsCreateExternalArrayBuffer | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 95459f9a9ff676f47d56ed584ad44a30f24fd4cb
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreateexternalarraybuffer-function"></a>Função JsCreateExternalArrayBuffer
Cria um objeto `ArrayBuffer` JavaScript para acessar a memória externa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `data`  
 Um ponteiro para a memória externa.  
  
 `byteLength`  
 O número de bytes na memória do sistema.  
  
 `finalizeCallback`  
 Um retorno de chamada para quando o objeto é finalizado. Pode ser nulo.  
  
 `callbackState`  
 Estado fornecido pelo usuário que será passado de volta para o finalizeCallback.  
  
 `result`  
 O novo objeto `ArrayBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
