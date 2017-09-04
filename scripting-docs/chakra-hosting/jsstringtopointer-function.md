---
title: "Função JsStringToPointer | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStringToPointer
helpviewer_keywords:
- JsStringToPointer function
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 7ff84f929833941fed9a709497dc615189c39386
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsstringtopointer-function"></a>Função JsStringToPointer
Recupera o ponteiro de cadeia de caracteres de um valor de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 O valor de cadeia de caracteres a converter em um ponteiro de cadeia de caracteres.  
  
 `stringValue`  
 O ponteiro de cadeia de caracteres.  
  
 `stringLength`  
 O comprimento da cadeia de caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Essa função recupera o ponteiro de cadeia de caracteres de um valor de cadeia de caracteres. Ela falhará com `JsErrorInvalidArgument` se o tipo do valor não for cadeia de caracteres. O tempo de vida da cadeia de caracteres retornada será o mesmo que o tempo de vida do respectivo valor de origem, porém, o ponteiro de cadeia de caracteres não é considerado uma referência para o valor (e, portanto, não impedirá que ele seja coletado).  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
