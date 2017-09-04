---
title: Typedef JsSerializedScriptUnloadCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsserializedscriptunloadcallback-typedef"></a>Typedef JsSerializedScriptUnloadCallback
Chamado pelo tempo de execução quando ele é concluído com todos os recursos relacionados à execução de script.     O chamador deve liberar a fonte se carregada, o código de bytes e o contexto nesse momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `sourceContext`  
 O contexto passado para `JsParseSerializedScriptWithCallback` ou `JsRunSerializedScriptWithCallback`.  
  
## <a name="remarks"></a>Comentários  
  
> [!WARNING]
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
