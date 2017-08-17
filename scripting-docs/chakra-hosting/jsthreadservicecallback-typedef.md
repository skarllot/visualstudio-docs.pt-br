---
title: Typedef JsThreadServiceCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsthreadservicecallback-typedef"></a>Typedef JsThreadServiceCallback
Um retorno de chamada de serviço de thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 callback  
 O retorno de chamada para o item de trabalho de plano de fundo.  
  
 callbackData  
 O argumento de dados a ser transmitido para o retorno de chamada.  
  
## <a name="remarks"></a>Comentários  
 O host pode especificar um serviço de thread de plano de fundo ao chamar JsCreateRuntime. Se especificado, os itens de trabalho de plano de fundo serão transmitidos usando esse retorno de chamada. Espera-se que o host comece a executar o item de trabalho de plano de fundo imediatamente, retornando true ou false, e o tempo de execução tratará o item de trabalho no thread.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
