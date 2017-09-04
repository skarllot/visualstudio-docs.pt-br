---
title: "Função JsInspectableToObject | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: dd0ad567-2ba8-4a63-bee4-2c6ff5ce9fa9
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: dc2c1cb12bf4b89d15e20a06c5366ac5fbc07faf
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsinspectabletoobject-function"></a>Função JsInspectableToObject
Cria um valor de JavaScript que é uma projeção do ponteiro `IInspectable` passado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsInspectableToObject(  
        _In_ IInspectable  *inspectable,  
        _Out_ JsValueRef *value  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `inspectable`  
 Um `IInspectable` a ser projetado.  
  
 `value`  
 Um valor de JavaScript que é uma projeção do `IInspectable`.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 O valor projetado pode ser usado pelo script para chamar um objeto WinRT. Hosts serão responsáveis por impor regras de threading do COM.  
  
 Exige um contexto de script ativo.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
