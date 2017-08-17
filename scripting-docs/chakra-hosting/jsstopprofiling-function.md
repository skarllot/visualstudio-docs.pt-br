---
title: "Função JsStopProfiling | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStopProfiling
helpviewer_keywords:
- JsStopProfiling function
ms.assetid: 3639c04f-a0f9-418b-be39-92f64b4e7ef8
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 0bed003e848a7ac34100a322275be04213da76e7
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsstopprofiling-function"></a>Função JsStopProfiling
Interrompe a criação de perfil no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsStopProfiling(  
   _In_ HRESULT reason  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `reason`  
 O motivo para interromper a criação de perfil a passar para o retorno de chamada do criador de perfil.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Não retornará um erro se a criação de perfil não foi iniciada.  
  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte em aplicativos de área de trabalho, mas não tem suporte em Aplicativos da Windows Store.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
