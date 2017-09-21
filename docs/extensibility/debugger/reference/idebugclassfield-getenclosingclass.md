---
title: IDebugClassField::GetEnclosingClass | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
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
ms.openlocfilehash: 6db4f9d43cfc655f199851afc1c9582bed0e2847
ms.lasthandoff: 02/22/2017

---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtém a classe que engloba essa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppClassField`  
 [out] Retorna um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) a classe de objeto que representa o delimitador. Retorna um valor nulo se não houver nenhuma classe delimitadora.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se a classe representado por este [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto é uma classe aninhada, o `ppClassField` parâmetro retorna um `IDebugClassField` a classe de objeto que representa o delimitador. Por exemplo, dada esta definição de classe:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Chamando o `GetEnclosingClass` método o `IDebugClassField` objeto representando o `NestedClass` classe retorna um `IDebugClassField` que representa a classe de objeto `RootClass`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
