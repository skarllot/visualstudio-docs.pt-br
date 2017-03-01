---
title: IDebugPropertyCreateEvent2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
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
ms.openlocfilehash: 74fe6f4a81ed91da5cbc9bcf9ea1f907b5d67bc1
ms.lasthandoff: 02/22/2017

---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando ele cria uma propriedade associada um documento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para informar que uma propriedade foi criada. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface. O SDM usa [QueryInterface](/visual-cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface. Essa interface é implementada se o DE ter criado uma propriedade associada a um script que foi carregado ou criado e se esse script precisa aparecer no IDE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para relatório de que uma propriedade foi criada. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele for anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra o método do `IDebugPropertyCreateEvent2` interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtém a nova propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Se uma propriedade tiver um documento específico ou script associado a ele, o DE pode enviar esse evento para o SDM para atualizar o **documentos de Script** janela com o nome do documento. O SDM chamará [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) com o argumento `guidDocument` para recuperar um `VARIANT` contendo um [IUnknown](/visual-cpp/atl/iunknown) ponteiro. O SDM chamará [QueryInterface](/visual-cpp/atl/queryinterface) esse ponteiro para recuperar o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface é usada para atualizar o **documentos de Script** janela.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
