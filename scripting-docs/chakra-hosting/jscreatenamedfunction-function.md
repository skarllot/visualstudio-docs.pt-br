---
title: "Função JsCreateNamedFunction | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 6a55f3df1d086394a7431b355f037b33e3f4a86c
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jscreatenamedfunction-function"></a>Função JsCreateNamedFunction
Cria uma nova função JavaScript nomeada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome dessa função que será usada para fins de diagnóstico e de transformação em cadeia de caracteres.  
  
 `nativeFunction`  
 O método a ser chamado quando a função é invocada.  
  
 `callbackState`  
 Estado fornecido pelo usuário que será passado de volta para o retorno de chamada.  
  
 `function`  
 O novo objeto de função.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
