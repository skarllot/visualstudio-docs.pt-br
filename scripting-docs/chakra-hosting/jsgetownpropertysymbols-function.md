---
title: "Função JsGetOwnPropertySymbols | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57c431e3-de0b-4ed0-b750-87a86448daff
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 5528acf52e16aa7b8896f3a69cc23465e23cb2b4
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetownpropertysymbols-function"></a>Função JsGetOwnPropertySymbols
Obtém a lista de todas as propriedades de símbolo no objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetOwnPropertySymbols(  
   _In_ JsValueRef object,  
   _Out_ JsValueRef *propertySymbols  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto do qual obter os símbolos de propriedade.  
  
 `propertySymbols`  
 Uma matriz de símbolos de propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
