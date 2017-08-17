---
title: "Função JsStartProfiling | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsStartProfiling
helpviewer_keywords:
- JsStartProfiling function
ms.assetid: 638da395-42dd-4fc5-b581-819e647e887d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 964e9f26de9cb5000884089da0b404b8d22fdd8d
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsstartprofiling-function"></a>Função JsStartProfiling
Inicia a criação de perfil no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsStartProfiling(  
   _In_ IActiveScriptProfilerCallback *callback,  
   _In_ PROFILER_EVENT_MASK eventMask,  
   _In_ unsigned long context  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `callback`  
 O retorno de chamada de criação de perfil a ser usado.  
  
 `eventMask`  
 Os eventos de criação de perfil com os quais realizar o retorno de chamada.  
  
 `context`  
 Um contexto a passar para o retorno de chamada de criação de perfil.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte em aplicativos de área de trabalho, mas não tem suporte em Aplicativos da Windows Store.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
