---
title: IEnumDebugPrograms2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
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
ms.openlocfilehash: bc24e767791c05ff601c86a24eb271696b64bf93
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Essa interface enumera os programas em execução na sessão de depuração atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para fornecer uma lista de programas que estão sendo depurado por DE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamadas do Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obter essa interface. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) não é usado pelo Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugPrograms2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera um número especificado de programas em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignora um número especificado de programas em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtém o número de programas em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 O Visual Studio usa essa interface para:  
  
-   Preencher o **módulos** janela (chamando [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) e, em seguida, chamar [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) em cada programa).  
  
-   Preencher o **anexar ao processo** lista (chamando `IDebugProcess2::EnumPrograms` e, em seguida, chamar [QueryInterface](/visual-cpp/atl/queryinterface) em cada [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface para obter uma [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interface).  
  
-   Gerar uma lista de DEs que pode depurar cada programa do processo (usando [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Aplicar atualizações de editar e continuar (ENC) para cada programa (chamando IDebugProcess2::EnumPrograms e, em seguida, chamar [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
