---
title: "Função JsCreateRuntime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsCreateRuntime
helpviewer_keywords:
- JsCreateRuntime function
ms.assetid: 92d09b89-6593-4d73-a562-88f9fec10228
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 93a3df1e7ea76cf76fad9ffde9ccea19f2ba28af
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreateruntime-function"></a>Função JsCreateRuntime
Cria um novo tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_ JsRuntimeVersion version,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `attributes`  
 Os atributos do tempo de execução a serem criados.  
  
 `version`  
 A versão do tempo de execução a ser criada.  
  
 `threadService`  
 O serviço de thread para o tempo de execução. Pode ser nulo.  
  
 `runtime`  
 O tempo de execução criado.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O parâmetro `version` não tem suporte no modo de borda. Para obter mais informações sobre como usar essa API no modo de borda, consulte [Borda de destino vs. mecanismos herdados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
