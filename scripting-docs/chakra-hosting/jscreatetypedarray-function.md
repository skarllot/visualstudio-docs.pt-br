---
title: "Função JsCreateTypedArray | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 1df33d0e1aadec9d7ed5aebf743e2c2f840e51fd
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreatetypedarray-function"></a>Função JsCreateTypedArray
Cria um objeto de matriz JavaScript tipada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `arrayType`  
 O tipo da matriz a criar.  
  
 `baseArray`  
 A matriz base da nova matriz. Use `JS_INVALID_REFERENCE` se não houver nenhuma matriz base.  
  
 `byteOffset`  
 O deslocamento em bytes do início do `baseArray` (`ArrayBuffer`) para a matriz tipada resultante a referenciar. Só aplicável quando `baseArray` é um objeto `ArrayBuffer`. Caso contrário, deve ser 0.  
  
 `elementLength`  
 O número de elementos na matriz. Aplicável somente ao criar uma nova matriz tipada sem `baseArray` (`baseArray` é `JS_INVALID_REFERENCE`) ou quando `baseArray` é um objeto `ArrayBuffer`. Caso contrário, deve ser 0.  
  
 `result`  
 O novo objeto de matriz tipada.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 A `baseArray` pode ser uma `ArrayBuffer`, outro tipo de matriz ou uma `Array` JavaScript. A matriz tipada retornada usará a `baseArray` se ela for um `ArrayBuffer` ou, caso contrário, criará e usará uma cópia da matriz de origem subjacente.  
  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
