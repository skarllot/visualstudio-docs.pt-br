---
title: Typedef JsPromiseContinuationCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jspromisecontinuationcallback-typedef"></a>Typedef JsPromiseContinuationCallback
Um retorno de chamada de continuação de promessa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>Comentários  
 O host pode especificar um retorno de chamada de continuação de promessa em `JsSetPromiseContinuationCallback`. Se um script cria uma tarefa para ser executada posteriormente, o retorno de chamada de continuação de promessa será chamado com a tarefa e a tarefa deverá ser colocada em uma fila PEPS, para ser executada quando a execução do script atual for concluída.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
