---
title: Anexo com base em Iniciar | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
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
ms.openlocfilehash: fe6384e9622fbe718f42e38cca3c003bf88fb2e9
ms.lasthandoff: 02/22/2017

---
# <a name="launch-based-attachment"></a>Anexo de lançamento
Baseado em inicialização anexo a um programa é automática. Quando o processo que hospeda o programa for iniciado, o SDM, baseado em inicialização anexo segue um caminho semelhante do método manual de anexo. Para obter informações, consulte [anexando o programa](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>O processo de anexar  
 A principal diferença é a sequência de eventos a seguir o **Attach** chamar, da seguinte maneira:  
  
1.  Enviar um **IDebugEngineCreateEvent2** o objeto de evento para o SDM. Para obter detalhes, consulte [enviando eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Chamar o `IDebugProgram2::GetProgramId` método o **IDebugProgram2** interface passada para o **Attach** método.  
  
3.  Enviar um **IDebugProgramCreateEvent2** o objeto de evento para notificar o SDM que local **IDebugProgram2** objeto foi criado para representar o programa para DE.  
  
4.  Enviar um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) o objeto de evento para notificar o SDM que um novo segmento é criado para o processo que o iniciou.  
  
## <a name="see-also"></a>Consulte também  
 [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)   
 [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
