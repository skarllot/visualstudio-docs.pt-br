---
title: "Função JsObjectToInspectable | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1d15b0b8-516f-4fc6-95aa-2ddd65f8ab75
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 4254269e39b64aa69b311be2991142f49343d196
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsobjecttoinspectable-function"></a>Função JsObjectToInspectable
Desencapsula um objeto de JavaScript para um ponteiro `IInspectable`  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsObjectToInspectable(  
   _In_ JsValueRef value,  
   _Out_ IInspectable  **inspectable  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 Um valor de JavaScript que deve ser projetado para `IInspectable`.  
  
 `inspectable`  
 Um valor de `IInspectable` do objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Hosts serão responsáveis por impor regras de threading do COM.  
  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
