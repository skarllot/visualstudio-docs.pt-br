---
title: IDebugModule3::LoadSymbols | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
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
ms.openlocfilehash: cfbbee570edb99e0158f2c37007e7435bece115f
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Carrega os símbolos para o módulo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```c#  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, ele retornará `S_OK`. Se ele falhar, ele retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método carrega os símbolos do caminho de pesquisa atual (que pode ser alterado, chamando o [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) método).  
  
 Esse método é preferencial sobre o [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
