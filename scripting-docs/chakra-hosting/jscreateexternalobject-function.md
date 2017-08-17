---
title: "Função JsCreateExternalObject | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsCreateExternalObject
helpviewer_keywords:
- JsCreateExternalObject function
ms.assetid: 6bcef506-93fb-429b-b06a-a971ff0b71f3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: f2b7b3d0f7cb4004d06de4b9b9258750e5d6f75b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreateexternalobject-function"></a>Função JsCreateExternalObject
Cria um novo objeto que armazena alguns dados externos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalObject(  
   _In_opt_ void *data,  
   _In_opt_ JsFinalizeCallback finalizeCallback,  
   _Out_ JsValueRef *object  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `data`  
 Dados externos que o objeto representará. Pode ser nulo.  
  
 `finalizeCallback`  
 Um retorno de chamada para quando o objeto é finalizado. Pode ser nulo.  
  
 `object`  
 O novo objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
