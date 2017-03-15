---
title: IDebugProcess3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
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
ms.openlocfilehash: a6228383df4a48f24d3409f5b63ee4c9c3f2eef9
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocess3"></a>IDebugProcess3
Essa interface representa um processo em execução e seus programas. Essa interface existe como uma substituição de vários métodos de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface. Ela fornece controle sobre todos os programas no processo.  
  
> [!NOTE]
>  [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), e [etapa](../../../extensibility/debugger/reference/idebugprogram2-step.md) métodos foram preteridos e não deve mais ser usados. Use os métodos correspondentes no `IDebugProcess3` interface em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por um fornecedor de porta personalizada para gerenciar programas como um grupo. Quando os programas são gerenciados como um grupo, você pode controlar sua execução e estabeleça uma linguagem para um avaliador de expressão. Esta interface deve ser implementada pelo fornecedor de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada principalmente pelo Gerenciador de depuração de sessão (SDM) para interagir com um grupo de programas identificados neste processo.  
  
 Chamar [QueryInterface](/visual-cpp/atl/queryinterface) em uma [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continua a execução de ou depurar um processo.|  
|[Executar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Inicia a execução de um processo.|  
|[Etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Etapas encaminham uma instrução ou instrução no processo.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtém o motivo que o processo foi iniciado para depuração.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Define o idioma de hospedagem para que o mecanismo de depuração possa carregar o avaliador de expressão apropriada.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera o idioma definido atualmente para esse processo.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Desabilita editar e continuar (ENC) para esse processo.<br /><br /> Um fornecedor de porta personalizada não implementar esse método (sempre deve retornar `E_NOTIMPL`).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obter o estado ENC para esse processo.<br /><br /> Um fornecedor de porta personalizada não implementar esse método (sempre deve retornar `E_NOTIMPL`).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera uma matriz de identificadores exclusivos para os mecanismos de depuração disponíveis.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
