---
title: "Função JsCreateDataView | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 1e5150a9b858e09217ee7ac3c1f25efba36615f9
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreatedataview-function"></a>Função JsCreateDataView
Cria um objeto `DataView` do JavaScript.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `arrayBuffer`  
 Um objeto `ArrayBuffer` existente a ser usado como o armazenamento para o objeto `DataView` resultante.  
  
 `byteOffset`  
 O deslocamento em bytes do início do `arrayBuffer` para o `DataView` resultante a referenciar.  
  
 `byteLength`  
 O número de bytes em ArrayBuffer para o DataView resultante a referenciar.  
  
 `result`  
 O novo objeto de DataView.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
