---
title: "Função JsGetTypedArrayInfo | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 44897f3960b09a110c1f1dd288f08bd5b9edc7ed
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgettypedarrayinfo-function"></a>Função JsGetTypedArrayInfo
Obtém as propriedades frequentemente usadas de uma matriz tipada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `typedArray`  
 A instância de matriz tipada.  
  
 `arrayType`  
 O tipo da matriz.  
  
 `arrayBuffer`  
 O repositório de backup `ArrayBuffer` da matriz.  
  
 `byteOffset`  
 O deslocamento em bytes do início do arrayBuffer referenciado pela matriz.  
  
 `byteLength`  
 O número de bytes na matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
