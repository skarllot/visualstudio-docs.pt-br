---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 3
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 5e0162d17fc81b1304213d0259863f35523a833f
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Anexa ao programa associado ou adia o processo de conexão para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidProgramId`  
 [in] `GUID` para atribuir ao programa associado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método não deve ser chamado. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado durante o processo de conexão, antes de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método é chamado. O `OnAttach` método pode executar o processo de conexão (nesse caso, este método retorna `S_FALSE`) ou adiar o processo de conexão para o `IDebugEngine2::Attach` método (o `OnAttach` retorna método `S_OK`). Em ambos os casos, o `OnAttach` método pode definir o `GUID` do programa que está sendo depurado a determinado `GUID`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
