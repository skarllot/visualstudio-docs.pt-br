---
title: IDebugCodeContext3 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 8
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
ms.openlocfilehash: da2e6011171afab54a055317c1ee9dc807200a02
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende o [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interface para habilitar a recuperação das interfaces do módulo e o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implementado pelos mecanismos de depuração e consumido pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pacote de depuração.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos de `IDebugCodeContext2` interface, essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera uma referência para a interface do módulo de depuração.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera uma referência para a interface do processo de depuração.|  
  
## <a name="remarks"></a>Comentários  
 Esta é uma interface opcional que geralmente não precisa ser implementado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
