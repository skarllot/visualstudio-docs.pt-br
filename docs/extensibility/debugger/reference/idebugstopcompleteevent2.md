---
title: IDebugStopCompleteEvent2 | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 6
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
ms.openlocfilehash: 55061440f4690c9b9f9b7a90dc5474391f908046
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
O mecanismo de depuração (DE) pode enviar esse evento opcional para o Gerenciador de sessão de depuração (SDM) quando um programa foi interrompido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Isso é uma nova interface para [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Versões anteriores não oferecia suporte a interrupção assíncrona.  
  
 [Parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) é chamado pelo SDM em vários processos ou programas vários cenários. Quando um programa envia um evento de parada para o SDM, o SDM solicitações de outros programas, muito.  
  
 Ele é usado para informar assincronamente o SDM um programa foi interrompido. Isso é útil para um mecanismo de depuração de intérprete, onde, às vezes, nenhum código é executado dentro do programa depurado, portanto [parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) não pode ser concluída de forma síncrona. Se um mecanismo de depuração deseja empregar essa notificação assíncrona, ela deve retornar `S_ASYNC_STOP` de [parar](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
