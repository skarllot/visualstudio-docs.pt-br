---
title: "Descrições de eventos | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
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
ms.openlocfilehash: 022b608171f30179952b37b866b2f4a581dd62b9
ms.lasthandoff: 02/22/2017

---
# <a name="event-descriptions"></a>Descrições de eventos
Cada tipo de evento tem uma finalidade específica.  
  
## <a name="events-and-the-reasons-for-their-use"></a>Eventos e os motivos para seu uso  
  
|Evento|Descrição|  
|-----------|-----------------|  
|Ativar eventos do documento|Ocorre quando o mecanismo de depuração (DE) deseja que o IDE para abrir ou colocar um documento para o primeiro plano.|  
|Ponto de interrupção associada ou eventos de erro do ponto de interrupção|Enviado quando está associado a um ponto de interrupção ou quando não é possível associar um ponto de interrupção e um erro será retornado.|  
|Eventos de ponto de interrupção não associado|Ocorre quando um ponto de interrupção associado desassocia do código.|  
|Pode interromper eventos|Enviada ao IDE para determinar se o usuário deseja parar em um ponto especificado no código.|  
|Eventos de ponto de interrupção|Ocorre quando um código ou dados de ponto de interrupção é atingido.|  
|Eventos de texto do documento|Ocorre quando o texto em um documento é alterado. Esses eventos não são enviados por meio de `IDebugEventCallBack2::Event` método.|  
|Mecanismo de criar eventos|Enviado quando um mecanismo é criado pela primeira vez.|  
|Eventos de ponto de entrada|Enviado quando o programa que está sendo depurado tem executar seu código de inicialização e atingiu o primeiro ponto de entrada do usuário.|  
|Eventos de exceção|Enviado quando um programa em execução atinge uma exceção.|  
|Eventos de conclusão de avaliação de expressão|Enviado quando a avaliação de expressão assíncrona for concluída.|  
|Localizar eventos de símbolo|Enviado sempre que o DE precisa perguntar ao usuário para localizar símbolos para um módulo.|  
|Eventos de conclusão de carga|Enviado apenas quando a carga do programa inicial for concluída e o código primeiro está prestes a ser executado no programa.|  
|Eventos de mensagem|Enviado quando mensagens são enviadas aos usuários.|  
|Eventos de módulo de carregamento|Enviado quando um novo módulo é carregado ou descarregado.|  
|Eventos de cadeia de caracteres de saída|Enviado quando o programa grava a saída de depuração.|  
|Criar e destruir eventos|Enviado para anunciar a criação ou destruição de processos, programas, propriedades, sessões e threads, portanto o IDE do Visual Studio pode acompanhar o estado dos programas que estão sendo depurados.|  
|Eventos de conclusão de etapa|Enviado quando uma etapa for concluída.|  
|Eventos de alteração do nome do thread|Enviado quando o usuário altera o nome de um thread.|  
|Eventos de alteração de nome de programa|Enviado quando o usuário altera o nome de um programa.|  
  
## <a name="see-also"></a>Consulte também  
 [Envio de eventos](../../extensibility/debugger/sending-events.md)
