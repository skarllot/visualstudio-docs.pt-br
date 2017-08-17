---
title: "Função JsGetDataViewStorage | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c2180e0-51d5-4cc8-ad21-8bf29ff7c583
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6b405fc22e411c343dcd5214495deb0275f5db52
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetdataviewstorage-function"></a>Função JsGetDataViewStorage
Obtém o armazenamento subjacente de memória usado por uma `DataView`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
STDAPI_(JsErrorCode) JsGetDataViewStorage(  
   _In_ JsValueRef dataView,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dataView`  
 A instância de DataView.  
  
 `buffer`  
 O buffer de DataView. O tempo de vida do buffer retornado é o mesmo que o tempo de vida da `DataView`. O ponteiro de buffer não conta como uma referência para a `DataView` para fins de coleta de lixo.  
  
 `bufferLength`  
 O número de bytes no buffer.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
