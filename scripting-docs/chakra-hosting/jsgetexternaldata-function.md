---
title: "Função JsGetExternalData | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsGetExternalData
helpviewer_keywords:
- JsGetExternalData function
ms.assetid: 1919e1da-3ea7-4269-a5fb-a3be06bd029b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: da78672f85159070949d067867699cfb5223b31c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsgetexternaldata-function"></a>Função JsGetExternalData
Recupera os dados de um objeto externo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsGetExternalData(  
   _In_ JsValueRef object,  
   _Out_ void **externalData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto externo.  
  
 `externalData`  
 Os dados externos armazenados no objeto. Pode ser nulo se não há dados externos armazenados no objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
