---
title: "Função JsIsRuntimeExecutionDisabled | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsIsRuntimeExecutionDisabled
helpviewer_keywords:
- JsIsRuntimeExecutionDisabled function
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: f4827205a33d337445faf9b0e9812133f0de3e97
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsisruntimeexecutiondisabled-function"></a>Função JsIsRuntimeExecutionDisabled
Retorna um valor que indica se a execução do script está desabilitada no tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(    _In_ JsRuntimeHandle runtime,    _Out_ bool *isDisabled);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `runtime`  
 Especifica o tempo de execução para verificar se a execução está desabilitada.  
  
 `isDisabled`  
 `true` se a execução for desabilitada, caso contrário, `false`.  
  
## <a name="return-value"></a>Valor de retorno  
 `JsNoError` se a operação for bem-sucedida, caso contrário, um código de falha.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
