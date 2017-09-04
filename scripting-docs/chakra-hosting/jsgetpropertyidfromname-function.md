---
title: "Função JsGetPropertyIdFromName | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetPropertyIdFromName
helpviewer_keywords:
- JsGetPropertyIdFromName function
ms.assetid: 1674906f-746a-4c62-99cd-023276683a86
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 3c8779999bf2d03ce1a7435ad55848b5acbdc601
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetpropertyidfromname-function"></a>Função JsGetPropertyIdFromName
Obtém a ID da propriedade associada ao nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromName(  
   _In_z_ const wchar_t *name,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome da propriedade a obter ou criar. O nome pode consistir apenas de dígitos.  
  
 `propertyId`  
 A ID da propriedade nesse tempo de execução para o nome fornecido.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 IDs de propriedade são específicas a um contexto e não podem ser usadas entre contextos.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
