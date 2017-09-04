---
title: "Enumeração JsErrorCode | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsErrorCode
helpviewer_keywords:
- JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.contentlocale: pt-br
ms.lasthandoff: 08/11/2017

---
# <a name="jserrorcode-enumeration"></a>Enumeração JsErrorCode
Um código de erro retornado de uma API de hospedagem Chakra.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Nome|Descrição|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|O contexto não pode ser colocado em um estado de depuração porque ele já está em um estado de depuração.|  
|`JsErrorAlreadyProfilingContext`|O contexto não é capaz de iniciar a criação de perfil porque ele já está executando essa atividade.|  
|`JsErrorArgumentNotObject`|Uma API de hospedagem que opera em valores de objeto foi chamada com um valor não objeto.|  
|`JsErrorBadSerializedScript`|Um script serializado incorreto foi usado ou o script serializado foi serializado por uma versão diferente do mecanismo de Chakra.|  
|`JsErrorCannotDisableExecution`|O tempo de execução não dá suporte a interrupção de script confiável.|  
|`JsErrorCannotSerializeDebugScript`|Scripts não podem ser serializados em contextos de depuração.|  
|`JsErrorCategoryEngine`|Categoria de erros que relaciona os erros que ocorrem dentro do mecanismo em si.|  
|`JsErrorCategoryFatal`|Categoria de erros fatais e significam falha do mecanismo.|  
|`JsErrorCategoryScript`|Categoria de erros relacionados a erros em um script.|  
|`JsErrorCategoryUsage`|Categoria de erros que se refere ao uso incorreto da API em si.|  
|`JsErrorFatal`|Ocorreu um erro fatal no mecanismo.|  
|`JsErrorHeapEnumInProgress`|Uma enumeração de heap está em andamento no contexto do script.|  
|`JsErrorIdleNotEnabled`|Notificação ociosa atribuída quando o host não habilitou o processamento ocioso.|  
|`JsErrorInDisabledState`|O tempo de execução está em um estado desabilitado.|  
|`JsErrorInExceptionState`|O mecanismo está em um estado de exceção e nenhuma API pode ser chamada até que a exceção seja limpa.|  
|`JsErrorInObjectBeforeCollectCallback`|Não há suporte para a operação em um objeto antes do retorno de chamada de coleta.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
|`JsErrorInProfileCallback`|Um contexto de script está no meio de um retorno de chamada de perfil.|  
|`JsErrorInThreadServiceCallback`|Um retorno de chamada de serviço de thread está em andamento.|  
|`JsErrorInvalidArgument`|Um argumento para uma API de hospedagem era inválido.|  
|`JsErrorNoCurrentContext`|A API de hospedagem requer que um contexto seja atual, mas não há nenhum contexto atual.|  
|`JsErrorNotImplemented`|Uma API de hospedagem ainda não foi implementada.|  
|`JsErrorNullArgument`|Um argumento para uma API de hospedagem era nulo em um contexto no qual nulo não é permitido.|  
|`JsErrorObjectNotInspectable`|O objeto não pode ser desencapsulado para o ponteiro `IInspectable`.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
|`JsErrorOutOfMemory`|O mecanismo Chakra ficou com memória insuficiente.|  
|`JsErrorPropertyNotSymbol`|Uma API de hospedagem que opera em IDs de propriedade de símbolo, mas foi chamada com uma ID de propriedade não símbolo. O código de erro é retornado por `JsGetSymbolFromPropertyId` se a função for chamada com uma ID de propriedade não símbolo.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
|`JsErrorPropertyNotString`|Uma API de hospedagem que opera em IDs de propriedade de cadeia de caracteres, mas foi chamada com uma ID de propriedade não cadeia de caracteres. O código de erro é retornado pelo `JsGetPropertyNamefromId` existente se a função for chamada com uma ID de propriedade não cadeia de caracteres.<br /><br /> Este valor de enumeração tem suporte somente no modo de borda.|  
|`JsErrorRuntimeInUse`|Um tempo de execução que ainda está em uso não pode ser descartado.|  
|`JsErrorScriptCompile`|O JavaScript falhou ao compilar.|  
|`JsErrorScriptEvalDisabled`|Um script foi encerrado porque ele tentou usar `eval` ou `function` e avaliação foi desabilitada.|  
|`JsErrorScriptException`|Ocorreu uma exceção de JavaScript durante a execução de um script.|  
|`JsErrorScriptTerminated`|Um script foi encerrado devido a uma solicitação para suspender um tempo de execução.|  
|`JsErrorWrongRuntime`|Uma API de hospedagem foi chamada com o objeto criado em um tempo de execução de JavaScript diferente.|  
|`JsErrorWrongThread`|Uma API de hospedagem foi chamada no thread errado.|  
|`JsNoError`|Código de erro de êxito.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)
