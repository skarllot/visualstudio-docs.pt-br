---
title: "Função JsSetRuntimeMemoryLimit | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetruntimememorylimit-function"></a>Função JsSetRuntimeMemoryLimit
Define o limite de memória atual para um tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `runtime`  
 O tempo de execução cujo limite de memória deve ser definido.  
  
 `memoryLimit`  
 O novo limite de memória de tempo de execução, em bytes ou -1 para nenhum limite de memória.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Um limite de memória fará com que qualquer operação que exceda o limite falhe com um erro de "memória insuficiente". Definir o limite de memória do tempo de execução como -1 significa que o tempo de execução não tem limite de memória. Os novos tempos de execução, por padrão, não têm limite de memória. Se o novo limite de memória exceder o uso atual, a chamada será bem-sucedida e quaisquer alocações futuras nesse tempo de execução falharão até que o uso de memória do tempo de execução fique abaixo do limite.  
  
 O limite de memória de um tempo de execução pode ser sempre definido, independentemente de o tempo de execução estar ou não ativo em outro thread.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
