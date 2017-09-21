---
title: IDebugProgram2::Terminate | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
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
ms.openlocfilehash: 5685f5a6263e23bfa8b03c9ccb25d20ce2b41613
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Encerra o programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```c#  
int Terminate();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se possível, o programa será encerrado e descarregado do processo; Caso contrário, o mecanismo de depuração (DE) executará qualquer limpeza necessária.  
  
 Esse método ou o [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) método é chamado pelo IDE, normalmente em resposta ao usuário parar depuração todos. A implementação desse método deve, idealmente, encerrar o programa dentro do processo. Se isso não for possível, o DE deve impedir que o programa seja executado mais nesse processo (e fazer qualquer limpeza necessária). Se o `IDebugProcess2::Terminate` método foi chamado pelo IDE, todo o processo será encerrado em algum momento após o `IDebugProgram2::Terminate` método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Encerrar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
