---
title: "Função JsGetPropertyIdFromSymbol | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 190fe4b9-352e-4b10-9d0e-6c6bbd6363e8
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: ab8150d9a56621366c75a50f004b26e1bc5d747b
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetpropertyidfromsymbol-function"></a>Função JsGetPropertyIdFromSymbol
Obtém a ID da propriedade associada ao símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromSymbol(  
   _In_ JsValueRef symbol,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `symbol`  
 O símbolo cuja ID da propriedade está sendo recuperada.  
  
 `propertyId`  
 A ID da propriedade para o símbolo fornecido.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 IDs de propriedade são específicas a um contexto e não podem ser usadas entre contextos.  
  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
