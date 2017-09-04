---
title: "Função JsGetIndexedPropertiesExternalData | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2c313163-3462-42fd-8dee-3dfb3ac7f43f
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 1c3e59c7a85a9edbaae93c90c59abf214da9cc4a
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetindexedpropertiesexternaldata-function"></a>Função JsGetIndexedPropertiesExternalData
Recupera as informações de dados externos de propriedades indexadas de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetIndexedPropertiesExternalData(  
   _In_ JsValueRef object,  
   _Out_ void** data,  
   _Out_ JsTypedArrayType* arrayType,  
   _Out_ unsigned int* elementLength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto.  
  
 `data`  
 O repositório de backup de dados externos para as propriedades indexadas do objeto.  
  
 `arrayType`  
 O tipo de elemento de matriz em dados externos.  
  
 `elementLength`  
 O número de elementos da matriz em dados externos.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
