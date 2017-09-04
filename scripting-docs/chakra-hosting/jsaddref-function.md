---
title: "Função JsAddRef | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsAddRef
helpviewer_keywords:
- JsAddRef function
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 8e55ab6643dd949b8b41962161f76648dba926e8
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsaddref-function"></a>Função JsAddRef
Adiciona uma referência a um objeto que passou por coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
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
 Isso só precisará ser chamado em identificadores `JsRef` que não forem ser armazenados em algum lugar na pilha. Chamar `JsAddRef` garante que o objeto ao qual `JsRef` se refere não será liberado até que `JsRelease` seja chamado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
