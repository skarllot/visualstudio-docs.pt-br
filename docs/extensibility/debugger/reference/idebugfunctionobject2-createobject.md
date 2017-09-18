---
title: IDebugFunctionObject2::CreateObject | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
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
ms.openlocfilehash: 3c91d1ad034a602e8555073f38f81d6ba83a993a
ms.lasthandoff: 02/22/2017

---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Cria um objeto que usa um construtor que recebe um valor de tempo limite e de configurações de sinalizador de avaliação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 [in] Um [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto que representa o construtor do objeto a ser criado.  
  
 `dwArgs`  
 [in] O número de parâmetros na `pArg` matriz. Representa o número de parâmetros passados para o construtor.  
  
 `pArgs`  
 [in] Uma matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representa os parâmetros passados para o construtor.  
  
 `dwEvalFlags`  
 [in] Uma combinação de sinalizadores do [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeração que especificam como a avaliação deve ser executada.  
  
 `dwTimeout`  
 [in] Tempo máximo, em milissegundos, para aguardar antes de retornar desse método. Use **infinito** para aguardar indefinidamente.  
  
 `ppObject`  
 [out] Retorna um **IDebugObject** que representa o objeto recém-criado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método para criar um objeto que representa uma instância de uma classe ou outro tipo complexo que exige um construtor, que é um parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
