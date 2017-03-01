---
title: IDebugEngine3::SetJustMyCodeState | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
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
ms.openlocfilehash: f73370f40d9f9b1a1ac98d92ca61445debd1a483
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Esse método informa ao mecanismo de depuração sobre as informações de estado JustMyCode.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```c#  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fUpdate`  
 [in] Diferente de zero (`TRUE`) para atualizar as informações atuais, zero (`FALSE`) para redefinir todas as informações (ignorando tudo definido anteriormente).  
  
 `dwModules`  
 [in] Número de estruturas de informações no`rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Matriz de [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) estruturas para usar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 JustMyCode é o conceito de depuração somente o código que pertence a um usuário e ignorando todos os código intermediário, como código do sistema — mesmo se o código-fonte está disponível para esse código do sistema.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
