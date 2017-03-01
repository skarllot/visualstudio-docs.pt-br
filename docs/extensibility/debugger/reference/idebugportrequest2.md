---
title: IDebugPortRequest2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
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
ms.openlocfilehash: fb7ba86f41d9522986474227d814b820ccdc8576
ms.lasthandoff: 02/22/2017

---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Essa interface descreve uma porta. Essa descrição é usada para adicionar a porta para um fornecedor de porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Visual Studio implementa essa interface no processo de obtenção de uma porta de depuração de um fornecedor de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é passada para [adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para criar uma porta de depuração. Uma chamada para [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) retorna essa interface, que representa a solicitação usada para criar a porta em primeiro lugar.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugPortRequest2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtém o nome da porta para criar.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um mecanismo de depuração não interage com um fornecedor de porta e não terá nenhum uso para essa interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
