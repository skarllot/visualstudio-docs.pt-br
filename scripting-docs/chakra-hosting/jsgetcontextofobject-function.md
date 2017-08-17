---
title: "Função JsGetContextOfObject | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cea6cdcd-790f-455c-af04-026af8ae2eb7
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: dca788493809a75423830e3ca8eae8d5c141b21d
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetcontextofobject-function"></a>Função JsGetContextOfObject
Obtém o contexto do script ao qual o objeto pertence.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetContextOfObject(  
  _In_ JsValueRef object,  
  _Out_ JsContextRef *context  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto do qual obter o contexto.  
  
 `context`  
 O contexto ao qual o objeto pertence.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
