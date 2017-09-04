---
title: "Função JsVariantToValue | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsVariantToValue
helpviewer_keywords:
- JsVariantToValue function
ms.assetid: e8f9eb8b-55b3-4b65-927e-cad5b482edee
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: fc778d87aab7e80e7c1b04a68c2d3b9c6fdd885a
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsvarianttovalue-function"></a>Função JsVariantToValue
Cria um valor de JavaScript que é uma projeção do `VARIANT` passado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsVariantToValue(  
   _In_ VARIANT *variant,  
   _Out_ JsValueRef *value  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `variant`  
 Um `VARIANT` a ser projetado.  
  
 `value`  
 Um valor de JavaScript que é uma projeção do `VARIANT`.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O valor projetado pode ser usado pelo script para chamar um objeto de automação COM do script. Hosts serão responsáveis por impor regras de threading do COM.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
