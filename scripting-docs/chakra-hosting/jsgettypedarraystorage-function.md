---
title: "Função JsGetTypedArrayStorage | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 5b6f4dc99c219c2ebba631c42493bc194148b497
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgettypedarraystorage-function"></a>Função JsGetTypedArrayStorage
Obtém o armazenamento subjacente de memória usado por uma matriz tipada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `typedArray`  
 A instância de matriz tipada.  
  
 `buffer`  
 O buffer da matriz. O tempo de vida do buffer retornado é o mesmo que o tempo de vida da matriz. O ponteiro de buffer não conta como uma referência para a matriz para fins de coleta de lixo.  
  
 `bufferLength`  
 O número de bytes no buffer.  
  
 `arrayType`  
 O tipo da matriz.  
  
 `elementSize`  
 O tamanho de um elemento da matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
