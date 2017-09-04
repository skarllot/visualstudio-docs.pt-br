---
title: "Função JsPointerToString | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsPointerToString
helpviewer_keywords:
- JsPointerToString function
ms.assetid: c71ce07e-4359-450c-afbf-a6ab7d48dddf
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: ac3d8ede644178527591b77fdb42f2b8c3e579b6
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jspointertostring-function"></a>Função JsPointerToString
Cria um valor de cadeia de caracteres de um ponteiro de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsPointerToString(  
   _In_reads_(stringLength) const wchar_t *stringValue,  
   _In_ size_t stringLength,  
   _Out_ JsValueRef *value  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stringValue`  
 O ponteiro de cadeia de caracteres a converter em um valor de cadeia de caracteres.  
  
 `stringLength`  
 O tamanho da cadeia de caracteres a ser convertida.  
  
 `value`  
 O novo valor da cadeia de caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
