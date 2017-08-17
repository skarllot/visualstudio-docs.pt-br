---
title: "Enumeração JsMemoryEventType | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsMemoryEventType
helpviewer_keywords:
- JsMemoryEventType enumeration
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: ef39008ba84337cebdc9613db17cc9fbdfc8aa79
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsmemoryeventtype-enumeration"></a>Enumeração JsMemoryEventType
Tipo de evento de retorno de chamada de alocação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum JsMemoryEventType;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Nome|Descrição|  
|----------|-----------------|  
|`JsMemoryAllocate`|Indica uma solicitação de alocação de memória.|  
|`JsMemoryFailure`|Indica um evento de falha de alocação.|  
|`JsMemoryFree`|Indica um evento de liberação de memória.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
