---
title: "Função JsCreateContext | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsCreateContext
helpviewer_keywords:
- JsCreateContext function
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: ee756158401468ee00007a764e18a0846f35a3dc
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreatecontext-function"></a>Função JsCreateContext
Cria um contexto de script para executar scripts.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `runtime`  
 O tempo de execução em que o contexto do script está sendo criado.  
  
 `debugApplication`  
 O aplicativo de depuração a ser usado para depuração. Esse parâmetro poderá ser nulo; se esse for o caso, a depuração não estará habilitada para o contexto.  
  
 `newContext`  
 O contexto do script criado.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O contexto de cada script tem seu próprio objeto global que é isolado de todos os outros contextos de script.  
  
 O parâmetro `debugApplication` não tem suporte no modo de borda. Para obter mais informações sobre como usar essa API no modo de borda, consulte [Borda de destino vs. mecanismos herdados](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
