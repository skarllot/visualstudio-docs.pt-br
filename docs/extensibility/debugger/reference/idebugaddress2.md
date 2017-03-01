---
title: IDebugAddress2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
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
ms.openlocfilehash: 005911465f7ba78a3a6dcdf8249a96443cd12355
ms.lasthandoff: 02/22/2017

---
# <a name="idebugaddress2"></a>IDebugAddress2
Essa interface fornece acesso para a identificação do processo que possui o objeto cujo endereço é representado por esta interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Essa interface fornece acesso para a identificação do processo que possui o objeto que está relacionado a esse endereço.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](/visual-cpp/atl/queryinterface) para obter essa interface da [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos em vtable ordem  
 Além dos métodos herdados do [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface, essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera a ID do processo que possui o objeto representado por esta interface.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
