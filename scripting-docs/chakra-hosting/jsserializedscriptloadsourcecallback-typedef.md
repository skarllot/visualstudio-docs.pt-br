---
title: Typedef JsSerializedScriptLoadSourceCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>Typedef JsSerializedScriptLoadSourceCallback
Chamado pelo tempo de execução para carregar o código-fonte do script serializado.     O chamador deve manter o buffer de script válido até o `JsSerializedScriptUnloadCallback`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `sourceContext`  
 O contexto passado para `JsParseSerializedScriptWithCallback` ou `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 O script retornado.  
  
## <a name="remarks"></a>Comentários  
  
> [!WARNING]
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
