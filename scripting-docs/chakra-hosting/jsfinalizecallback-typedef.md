---
title: Typedef JsFinalizeCallback | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa7a0269-b9d4-4717-97ac-8da7eb6ced15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6efb6873e1bfc6c8689c0ae7939bb11cc7b311bf
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsfinalizecallback-typedef"></a>Typedef JsFinalizeCallback
Um retorno de chamada finalizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void (CALLBACK *JsFinalizeCallback)(  
   _In_opt_ void *data  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Dados  
 Os dados externos que foram passados ao criar o objeto que está sendo finalizado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
