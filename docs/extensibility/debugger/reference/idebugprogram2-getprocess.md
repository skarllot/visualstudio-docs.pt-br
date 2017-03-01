---
title: IDebugProgram2::GetProcess | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
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
ms.openlocfilehash: bb752757619796b53354bfcf7257eaadde78b8be
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obter o processo que o programa é executado no.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```c#  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppProcess`  
 [out] Retorna o [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface que representa o processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A menos que implementa um mecanismo de depuração (DE) o [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interface, a implementação do desse método deve retornar sempre `E_NOTIMPL` porque a DE não pode determinar qual processo está em execução em e, portanto, não é possível atender a uma implementação do método.  
  
 Implementando o `IDebugEngineLaunch2` interface significa que o DE deve saber como criar um processo; portanto, a implementação do do [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface é capaz de saber qual processo está em execução no.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
