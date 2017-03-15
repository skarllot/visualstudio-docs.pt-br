---
title: IDebugDynamicField | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
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
ms.openlocfilehash: 27b118b43d5ba801a668480dd0abaa084e7905ae
ms.lasthandoff: 02/22/2017

---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Essa interface representa um tipo de uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por provedores de símbolo como uma classe base para qualquer tipo que pode ser determinada em tempo de execução. Isso é apenas para código gerenciado.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface representa uma classe base da qual interfaces mais especializadas podem ser derivadas.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Essa interface não fornece quaisquer métodos diferentes de aquelas herdadas do `IDebugField`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
