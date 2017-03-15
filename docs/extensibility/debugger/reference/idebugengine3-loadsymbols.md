---
title: IDebugEngine3::LoadSymbols | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
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
ms.openlocfilehash: 5555264d7cd63c612ce2cbde13c5ccdda63c056c
ms.lasthandoff: 02/22/2017

---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Símbolos de cargas (conforme necessário) para todos os módulos que está sendo depurados por este mecanismo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Isso carrega os símbolos de depuração para todos os módulos referenciados por esse mecanismo de depuração. Os símbolos são carregados somente se eles ainda não foram carregados. Símbolos são pesquisados nos caminhos definidos por uma chamada para [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Consulte também  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
