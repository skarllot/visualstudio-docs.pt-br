---
title: "Função JsCreateURIError | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsCreateURIError
helpviewer_keywords:
- JsCreateURIError function
ms.assetid: 711fd237-12a2-4ff0-b58a-ad74c91e79fb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 9750f9a554cd442c26a45fcc97e70273b15df9ac
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreateurierror-function"></a>Função JsCreateURIError
Cria um novo objeto de erro URIError do JavaScript  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsCreateURIError(  
   _In_ JsValueRef message,  
   _Out_ JsValueRef *error  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `message`  
 Mensagem para o objeto de erro.  
  
 `error`  
 O novo objeto de erro.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
