---
title: "Enviar os eventos necessários | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
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
ms.openlocfilehash: 1d8fb45da61ece3a4b55d7084c42e5326ab34e6a
ms.lasthandoff: 02/22/2017

---
# <a name="sending-the-required-events"></a>Enviar os eventos necessários
Use este procedimento para enviar eventos necessários.  
  
## <a name="process-for-sending-required-events"></a>Processo de envio de eventos necessários  
 Os eventos a seguir são necessários, em ordem, quando criar uma depuração mecanismo (DE) e anexá-lo a um programa:  
  
1.  Enviar um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) o objeto de evento para o Gerenciador de sessão de depuração (SDM) quando o DE é inicializado para um ou mais programas em um processo de depuração.  
  
2.  Quando o programa a ser depurado é conectado, enviar um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) o objeto de evento para o SDM. Esse evento pode ser um evento de parada, dependendo de seu design de mecanismo.  
  
3.  Se o programa é conectado quando o processo é iniciado, envie um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) o objeto de evento para o SDM para notificar o IDE do novo thread. Esse evento pode ser um evento de parada, dependendo de seu design de mecanismo.  
  
4.  Enviar um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o objeto de evento para o SDM quando o programa que está sendo depurado está carregamento concluído ou quando anexando o programa for concluído. Esse evento deve ser um evento de parada.  
  
5.  Se o aplicativo a ser depurado é iniciado, envie um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) o objeto de evento para o SDM quando a primeira instrução de código na arquitetura do tempo de execução está prestes a ser executada. Esse evento é sempre um evento de parada. Quando examinarmos a sessão de depuração, o IDE para esse evento.  
  
> [!NOTE]
>  Muitas linguagens usam inicializadores global ou funções externas, pré-compilados (da biblioteca CRT ou Main) no início do seu código. Se o idioma do programa que você está depurando contém qualquer um desses tipos de elementos antes do ponto de entrada inicial, esse código é executado e o evento de ponto de entrada é enviado quando o usuário ponto de entrada, como **principal** ou `WinMain`, for atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
