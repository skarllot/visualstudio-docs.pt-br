---
title: "Função JsGetContextData | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5d7e446-267a-4a80-a427-6e1b95a3391b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 7e96bbca6fed13708a1df895819af2285c80918b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetcontextdata-function"></a>Função JsGetContextData
Obtém os dados internos definidos em JsrtContext.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetContextData(  
  _In_ JsContextRef context,  
  _Out_ void **data  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `context`  
 O contexto do qual obter os dados.  
  
 `data`  
 O ponteiro para os dados em que os dados serão retornados.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
