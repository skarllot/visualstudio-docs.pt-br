---
title: "Função JsDefineProperty | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsDefineProperty
helpviewer_keywords:
- JsDefineProperty function
ms.assetid: b2cf48d6-eb40-457c-aa8b-b16a50dc5d6a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 3f929dd875b2ba8bf95db8d5970a770ce2859484
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsdefineproperty-function"></a>Função JsDefineProperty
Define a propriedade de um novo objeto por meio de um descritor de propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsDefineProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ JsValueRef propertyDescriptor,  
   _Out_ bool *result  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto que tem a propriedade.  
  
 `propertyId`  
 ID da propriedade.  
  
 `propertyDescriptor`  
 O descritor da propriedade.  
  
 `result`  
 Se a propriedade foi ou não definida.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
