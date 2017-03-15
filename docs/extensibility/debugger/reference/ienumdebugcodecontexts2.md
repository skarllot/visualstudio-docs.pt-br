---
title: IEnumDebugCodeContexts2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
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
ms.openlocfilehash: 9d76e65829d8e88a2e5bb9487d1acf1bb5efdda7
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Essa interface enumera os contextos de código associados com a sessão de depuração, ou com um determinado programa ou documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de contextos de código para uma posição de texto específico em um programa ou uma lista de contextos de código de um contexto de documento específico.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para obter essa interface que representa uma lista de contextos de código para uma posição de um texto específico no documento de origem do programa.  
  
 Chamar [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) para obter essa interface que representa uma lista de todos os contextos de código em um documento de origem em particular.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugCodeContexts2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera um número especificado de contextos de código em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignora um número especificado de contextos de código em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtém o número de contextos de código em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 Chamadas do Visual Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para preencher uma lista de contextos de código, o usuário pode escolher de quando definir próxima instrução ou mostrar a desmontagem de um arquivo de origem. Vários contextos de código podem ocorrer, por exemplo, quando há várias instâncias de um modelo de estilo C++.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
