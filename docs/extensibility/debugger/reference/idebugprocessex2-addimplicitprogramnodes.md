---
title: IDebugProcessEx2::AddImplicitProgramNodes | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
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
ms.openlocfilehash: cc4f2f9908826712ebb65ad1f8c22680226ecb54
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Este método adiciona um nó de programa para cada mecanismo de depuração (DE) especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidLaunchingEngine`  
 [in] O `GUID` de um DE que deve ser usado para iniciar programas (e é considerado como para adicionar seus próprio programa nós).  
  
 `rgguidSpecificEngines`  
 [in] Matriz de `GUID`s de DEs qual programa nós serão adicionados.  
  
 `celtSpecificEngines`  
 [in] O número de `GUID`s na `rgguidSpecificEngines` matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 [Programa nós](../../../extensibility/debugger/program-nodes.md) serão adicionados para cada DE listado na `rgguidSpecificEngines`— exceto o mecanismo de inicialização (conforme indicado nos `guidLaunchingEngine`), que é considerado como para adicionar seu próprio nó programa quando ele inicia um programa.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nós de programa](../../../extensibility/debugger/program-nodes.md)
