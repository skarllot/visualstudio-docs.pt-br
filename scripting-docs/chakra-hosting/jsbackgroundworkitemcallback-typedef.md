---
title: Typedef JsBackgroundWorkItemCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 5c4281ae1abf1df07d4b6374b6989377c66c1fd7
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsbackgroundworkitemcallback-typedef"></a>Typedef JsBackgroundWorkItemCallback
Um retorno de chamada de item de trabalho de plano de fundo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 callbackData  
 Argumento de dados transmitido ao serviço de thread.  
  
## <a name="remarks"></a>Comentários  
 É transmitido ao serviço de thread do host (se fornecido) para permitir que o host invoque o retorno de chamada do item de trabalho no thread do plano de fundo de sua escolha.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
