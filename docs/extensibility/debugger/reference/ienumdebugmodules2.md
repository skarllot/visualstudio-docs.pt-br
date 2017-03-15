---
title: IEnumDebugModules2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
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
ms.openlocfilehash: 69dfd5b565722fab4ecab9b13c5d2ef78837d621
ms.lasthandoff: 02/22/2017

---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Essa interface enumera uma lista de módulos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de módulos carregados para um programa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamadas do Visual Studio [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugModules2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Recupera um número especificado de módulos em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignora um número especificado de módulos em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Obtém o número de módulos.|  
  
## <a name="remarks"></a>Comentários  
 O Visual Studio usa essa interface principalmente para atualizar o **módulos** janela.  
  
 Para fins de depuração no Visual Studio, um programa é uma sequência lógica de instruções de código que pode cruzar os limites do módulo, portanto, a necessidade de uma lista dos módulos de um único [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface. O primeiro módulo na lista normalmente contém o ponto de entrada inicial para o programa associado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
