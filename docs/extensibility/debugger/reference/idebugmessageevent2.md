---
title: IDebugMessageEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: dfbe6b139a823fa13e9ce58284026c163cc07ffa
ms.lasthandoff: 04/05/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Essa interface é usada pelo mecanismo de depuração (DE) para enviar uma mensagem para o Visual Studio que requer uma resposta do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para enviar uma mensagem para o Visual Studio que requer uma resposta do usuário. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface. Usa o SDM [QueryInterface](/cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface.  
  
 A implementação desta interface deve se comunicar a chamada do Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) para DE. Por exemplo, isso pode ser feito com uma mensagem postada a mensagem do DE segmento de tratamento ou o objeto que implementa essa interface pode conter uma referência para o DE e retorno de chamada para o DE com a resposta passada para `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para exibir uma mensagem para o usuário que solicita uma resposta. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugMessageEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtém a mensagem a ser exibida.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Define a resposta, se houver, na caixa de mensagem.|  
  
## <a name="remarks"></a>Comentários  
 O DE usará essa interface se ele requer uma resposta específica do usuário para uma determinada mensagem. Por exemplo, se o DE receber uma mensagem de "Acesso negado" após uma tentativa de se conectar remotamente a um programa, o DE envia a mensagem em questão para o Visual Studio em um `IDebugMessageEvent2` evento com o estilo de caixa de mensagem `MB_RETRYCANCEL`. Isso permite que o usuário tentar novamente ou cancelar a operação de anexação.  
  
 O DE Especifica como esta mensagem deve ser tratada pelo segue as convenções da função Win32 `MessageBox` (consulte [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) para obter detalhes).  
  
 Use o [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interface para enviar mensagens para o Visual Studio que não exigem uma resposta do usuário.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
