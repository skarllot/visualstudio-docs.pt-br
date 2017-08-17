---
title: Typedef JsRuntimeHandle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: d3c0344e203c58691048c55ba4080c6c86c1c643
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsruntimehandle-typedef"></a>Typedef JsRuntimeHandle
Um identificador para um tempo de execução Chakra.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## <a name="remarks"></a>Comentários  
 Cada tempo de execução Chakra tem seu próprio mecanismo de execução independente, compilador JIT e heap com coleta de lixo. Dessa forma, cada tempo de execução fica completamente isolado de outros tempos de execução.  
  
 Os tempos de execução podem ser usados em qualquer thread, mas apenas um thread pode chamar um tempo de execução a qualquer momento.  
  
> [!WARNING]
>  Um JsRuntimeHandle, diferente de outras referências de objeto na API de hospedagem Chakra, não é lixo coletado porque contém o heap com coleta de lixo em si. A execução continuará a existir até o JsDisposeRuntime ser chamado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
