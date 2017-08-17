---
title: "Função JsGetPropertyNameFromId | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetPropertyNameFromId
helpviewer_keywords:
- JsGetPropertyNameFromId function
ms.assetid: b4ca442c-573d-4bc3-adf7-1b8d48480b3a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 9f14851a52f4e6de1e2702ad11eab20bf448a048
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetpropertynamefromid-function"></a>Função JsGetPropertyNameFromId
Obtém o nome associado à ID da propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyNameFromId(  
   _In_ JsPropertyIdRef propertyId,  
   _Outptr_result_z_ const wchar_t **name  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `propertyId`  
 A ID de propriedade da qual obter o nome.  
  
 `name`  
 O nome associado à ID da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 O buffer retornado é válido desde que o tempo de execução esteja ativo e não pode ser usado após o tempo de execução ser descartado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
