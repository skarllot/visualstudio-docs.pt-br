---
title: IDebugThread2::CanSetNextStatement | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
caps.latest.revision: 9
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
ms.openlocfilehash: 0b7ff8319bd1c8fddf53c3a58eed604bc8e4cc0f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
Determina se o ponteiro de instrução atual pode ser definido para o quadro de pilha determinado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStackFrame`  
 Reservado para uso futuro; Defina como um valor nulo. Se esse for um valor nulo, use o quadro de pilha atual.  
  
 `pCodeContext`  
 [in] Um [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que descreve o local do código prestes a ser executada e seu contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se esse método retornar `S_OK`, em seguida, chame o [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) método realmente definir próxima instrução.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
