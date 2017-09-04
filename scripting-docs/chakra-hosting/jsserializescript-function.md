---
title: "Função JsSerializeScript | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsSerializeScript
helpviewer_keywords:
- JsSerializeScript function
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: 92bc6c1de0f2cd43dfe9566413fb64188fd5a382
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsserializescript-function"></a>Função JsSerializeScript
Serializa um script analisado para um buffer que pode ser reutilizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `script`  
 O script a serializar.  
  
 `buffer`  
 O buffer no qual colocar o script serializado. Pode ser nulo.  
  
 `bufferSize`  
 Em entrada, o tamanho do buffer, em bytes; em saída, o tamanho do buffer, em bytes, necessário para conter o script serializado.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 `JsSerializeScript` analisa um script e, em seguida, armazena a forma analisada do script em um formato independente de tempo de execução. O script serializado, em seguida, pode ser desserializado em qualquer tempo de execução sem a necessidade de reanalisar o script.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
