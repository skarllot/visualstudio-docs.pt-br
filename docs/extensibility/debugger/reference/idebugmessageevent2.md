---
title: IDebugMessageEvent2 | Documentos do Microsoft
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 0f033c5793dc3b89a1f2bd74a2bc4857730fb746
ms.lasthandoff: 02/22/2017

---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Essa interface é usada pelo mecanismo de depuração (DE) para enviar uma mensagem para o Visual Studio que requer uma resposta do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugMessageEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para enviar uma mensagem para o Visual Studio que requer uma resposta do usuário. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface. O SDM usa [QueryInterface](/visual-cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface.  
  
 A implementação dessa interface deve se comunicar a chamada do Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) para DE. Por exemplo, isso pode ser feito com uma mensagem publicada à mensagem do DE tratamento de segmento ou o objeto que implementa essa interface pode manter uma referência para o DE e chamar de volta o DE com a resposta passada em `IDebugMessageEvent2::SetResponse`.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para exibir uma mensagem para o usuário que solicita uma resposta. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele for anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugMessageEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtém a mensagem a ser exibida.|  
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Define a resposta, se houver, da caixa de mensagem.|  
  
## <a name="remarks"></a>Comentários  
 O DE usará essa interface se ela exige uma resposta específica do usuário para uma determinada mensagem. Por exemplo, se o DE uma mensagem de "Acesso negado" após uma tentativa de se conectar remotamente a um programa, o DE envia essa mensagem específica para o Visual Studio em uma `IDebugMessageEvent2` eventos com o estilo de caixa de mensagem `MB_RETRYCANCEL`. Isso permite que o usuário tentar novamente ou cancelar a operação de anexação.  
  
 O DE Especifica como esta mensagem deve ser tratada seguindo as convenções da função Win32 `MessageBox` (consulte [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) para obter detalhes).  
  
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
