---
title: Envio de eventos | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
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
ms.openlocfilehash: edd4abfa31b309290bdb07fd98c104a279d98fc7
ms.lasthandoff: 02/22/2017

---
# <a name="sending-events"></a>Envio de eventos
O mecanismo para comunicação entre o depurador e o mecanismo de depuração (DE) é um modelo de evento com base no DCOM. Os eventos são enviados como objetos COM, e cada evento tem parâmetros que especificam o seguinte:  
  
-   O DE que o evento de chamada.  
  
-   Uma descrição do que aconteceu.  
  
-   O processo, programa e informações de thread que identifica o contexto de onde o evento ocorreu. O processo não é enviado por eventos enviados a partir DE.  
  
-   O tipo de evento que indica se o evento é síncrona ou assíncrona.  
  
 Todos os eventos de depuração são enviados usando o método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Fontes de evento](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explica as duas origens de eventos: o mecanismo de depuração (DE) e a sessão de depuração manager (SDM).  
  
 [Tipos de eventos com suporte](../../extensibility/debugger/supported-event-types.md)  
 Discute os tipos de eventos com suporte no momento: síncrono e assíncrono.  
  
 [Descrições de eventos](../../extensibility/debugger/event-descriptions.md)  
 Define os eventos e os motivos para seu uso.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Descreve como a DE funciona com o sistema operacional ou interpretador para fornecer serviços de depuração.
