---
title: IDebugProgram2::GetProgramId | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
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
ms.openlocfilehash: 9f92fd5dd6fa60a1fae789416b26c02a0e85e54a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Obtém um GUID para este programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```c#  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pguidProgramId`  
 [out] Retorna o `GUID` para este programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de depuração (DE) deve retornar o identificador de programa originalmente passado para o [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos. Isso permite a identificação do programa entre depurador componentes.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
