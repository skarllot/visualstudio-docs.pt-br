---
title: "Função JsInstanceOf | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94399a62-b996-4fd2-82ce-1c26e7a4da08
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 00b5018ae3d04e6bcb361b1c765df61e5855d553
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsinstanceof-function"></a>Função JsInstanceOf
Executa o teste do operador "instanceof" do JavaScript.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
JsInstanceOf(   
  _In_ JsValueRef object,  
  _In_ JsValueRef constructor,  
  _Out_ bool *result  
);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 O objeto a ser testado.  
  
 `constructor`  
 A função de construtor para a qual testar.  
  
 `result`  
 Se o "object instanceof constructor" é true.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
