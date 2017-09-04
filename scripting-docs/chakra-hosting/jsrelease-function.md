---
title: "Função JsRelease | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsRelease
helpviewer_keywords:
- JsRelease function
ms.assetid: 8714fd0b-5b66-48e0-927e-7b93af6cde7b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: cd5dda0eaa8cd6767991eea3f2a1cf9c70c65a27
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsrelease-function"></a>Função JsRelease
Libera uma referência a um objeto que passou por coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsRelease(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ref`  
 O objeto ao qual adicionar uma referência.  
  
 `count`  
 A nova contagem de referências do objeto (pode passar nulo).  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Remove uma referência a um identificador `JsRef` que foi criado por `JsAddRef`.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
