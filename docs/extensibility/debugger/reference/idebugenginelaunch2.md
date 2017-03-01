---
title: IDebugEngineLaunch2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
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
ms.openlocfilehash: 79f6b7c070a33834fb4127ca74873f1ac3d4d053
ms.lasthandoff: 02/22/2017

---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Usado por um mecanismo de depuração (DE) para iniciar e encerrar programas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por um personalizado DE se ele tiver requisitos especiais para iniciar um processo que não pode ser manipulado inteiramente por uma porta personalizada. Isso é geralmente o caso quando o DE é parte de um interpretador e o processo que está sendo depurado é um script: o interpretador precisa ser iniciado primeiro e, em seguida, o script é carregado e iniciado. Uma porta pode iniciar o interpretador, mas o script pode exigir tratamento especial (que é onde o DE tem uma função). Essa interface é implementada somente se houver requisitos exclusivos para iniciar um programa que não é possível lidar com uma porta personalizada.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada, o Gerenciador de sessão de depuração (SDM) se o SDM pode obter essa interface do [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (usando QueryInterface) da interface. Se essa interface pode ser obtida, o SDM sabe que o DE tiver requisitos especiais e chama essa interface para iniciar o programa em vez de ter a porta iniciá-lo.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugEngineLaunch2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Inicia um processo por meio DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Execução do processo de currículos.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Determina se um processo pode ser encerrado.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Finaliza um processo.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
