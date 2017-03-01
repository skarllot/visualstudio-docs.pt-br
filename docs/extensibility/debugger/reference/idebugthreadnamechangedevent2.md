---
title: IDebugThreadNameChangedEvent2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThreadNameChangedEvent2
helpviewer_keywords:
- IDebugThreadNameChangedEvent2
ms.assetid: 34c1652e-f019-48ba-8b26-ace20f8a158c
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
ms.openlocfilehash: d57362fa76e5131976a72a77dc030e7a2b117d62
ms.lasthandoff: 02/22/2017

---
# <a name="idebugthreadnamechangedevent2"></a>IDebugThreadNameChangedEvent2
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando um nome de thread muda no programa que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugThreadNameChangedEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para relatórios que alterou o nome do thread. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface. O SDM usa [QueryInterface](/visual-cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para relatório mudou o nome do thread. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele for anexado ao programa que está sendo depurado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
