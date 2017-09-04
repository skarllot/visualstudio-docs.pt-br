---
title: "Função JsSetProperty | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSetProperty
helpviewer_keywords:
- JsSetProperty function
ms.assetid: 2c36bebf-ec86-425c-8131-2dd75fd30f40
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 0930b0b3e59e2ea35f85295e2adc2cc5fdda33e1
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jssetproperty-function"></a>Função JsSetProperty
Coloca a propriedade de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetProperty(  
   _In_ JsValueRef object,  
   _In_ JsPropertyIdRef propertyId,  
   _In_ JsValueRef value,  
   _In_ bool useStrictRules  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto que contém a propriedade.  
  
 `propertyId`  
 ID da propriedade.  
  
 `value`  
 O novo valor da propriedade.  
  
 `useStrictRules`  
 A propriedade definida deve seguir as regras de modo estrito.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
