---
title: "Pacote de depuração | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
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
ms.openlocfilehash: 8e1ffa6cfbceabf166b2e104c04dee4f156f911c
ms.lasthandoff: 02/22/2017

---
# <a name="debug-package"></a>Pacote de depuração
O pacote de depuração é executado no shell do Visual Studio e manipula toda a interface do usuário. Ele consome interfaces de depuração do Visual Studio e se comunica com o Gerenciador de sessão de depuração (SDM).  
  
 Eventos de interrupção enviados por meio do SDM alternar o depurador de modo de execução para o modo de interrupção e alterar o foco para o programa onde a quebra ocorreu. O pacote de depuração controla o quadro de pilha e thread das informações enviadas a ele pelos eventos.  
  
 O pacote de depuração não tem idioma ou dependências de tempo de execução. Não é necessário implementar ou modificar o pacote de depuração.  
  
 O pacote de depuração é implementado pelo vsdebug.dll.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciador de sessão de depuração](../../extensibility/debugger/session-debug-manager.md)   
 [Quadros de pilha](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
