---
title: IDebugBinder3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBinder3
helpviewer_keywords:
- IDebugBinder3 interface
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 17be0ab2d5b42410777433fe23e4408857ba53fd
ms.lasthandoff: 02/22/2017

---
# <a name="idebugbinder3"></a>IDebugBinder3
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão do CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface fornece acesso aos tipos, aliases e serviços de visualizador personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um mecanismo de depuração implementa essa interface para oferecer suporte a aliases, serviços de visualizador personalizado e acesso a informações de tipo de objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface obtém essa interface usando [QueryInterface](/visual-cpp/atl/queryinterface).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos fornecidos pelo [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface, essa interface implementa o seguinte:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Recupera um objeto de memória que representa a memória ao qual esse objeto está associado.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Recupera a exceção associada a esse objeto (se houver)|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Recupera um alias recebe seu nome,|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Recupera uma matriz de todos os aliases para este objeto|  
|[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)|Obtém o número de tipos de argumento associado a este objeto|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Recupera uma lista de tipos de argumento associado a este objeto|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtém uma interface para um serviço de Visualizador|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Converte um objeto local ou um endereço de memória de 64 bits em um contexto de memória.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
