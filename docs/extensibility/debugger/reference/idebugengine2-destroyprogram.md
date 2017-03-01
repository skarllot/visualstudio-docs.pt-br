---
title: IDebugEngine2::DestroyProgram | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 10
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
ms.openlocfilehash: 735e0df77769b5f386f8c9409530154bce0c9847
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
Informa um mecanismo de depuração (DE) que o programa especificado foi encerrado atypically e que o DE limpar todas as referências para o programa e enviar um programa destruir o evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProgram`  
 [in] Um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa atypically foi encerrado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que esse método é chamado, o DE subsequentemente envia uma [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) eventos para o Gerenciador de sessão de depuração (SDM).  
  
 Este método não está implementado (retorna `E_NOTIMPL`) se o DE é executado no mesmo processo que o programa que está sendo depurado. Esse método é implementado somente se o DE é executado no mesmo processo que o SDM.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
