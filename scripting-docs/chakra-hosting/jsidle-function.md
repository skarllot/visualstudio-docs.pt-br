---
title: "Função JsIdle | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsIdle
helpviewer_keywords:
- JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jsidle-function"></a>Função JsIdle
Indica ao tempo de execução para fazer qualquer processamento ocioso que precise fazer.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nextIdleTick`  
 O próximo tique de sistema quando haverá mais trabalho ocioso a fazer. Pode ser nulo. Retorna o número máximo de tiques se não há trabalho ocioso futuro a fazer.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Se o processamento ocioso foi habilitado para o tempo de execução atual, chamar `JsIdle` informa ao tempo de execução atual que o host está ocioso e que o tempo de execução pode executar tarefas de limpeza de memória.  
  
 `JsIdle` também pode retornar o número de tiques do sistema até que haja mais trabalho ocioso a ser feito pelo tempo de execução. Chamar `JsIdle` antes que esse número de tiques tenha passado não fará nenhum trabalho.  
  
 Exige um contexto de script ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
