---
title: "Função JsNumberToInt | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: f24acb837fdf46694aa2370e2ccf1fe3c926ce19
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsnumbertoint-function"></a>Função JsNumberToInt
Recupera o valor de `int` de um valor numérico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 O valor numérico a converter em um valor `int`.  
  
 `intValue`  
 O valor `int`.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Essa função recupera o valor de um valor numérico e converte-o em um valor `int`. Ela falhará com `JsErrorInvalidArgument` se o tipo do valor não for numérico.  
  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
