---
title: Criar um personalizado Debug Engine | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 15
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
ms.openlocfilehash: 791ca7fddc982938f8adde0b2f126d3b4a4c61a4
ms.lasthandoff: 02/22/2017

---
# <a name="creating-a-custom-debug-engine"></a>Criando um mecanismo de depuração personalizado
Um mecanismo de depuração (DE) é um componente que permite a depuração de arquiteturas de tempo de execução específicas. Normalmente, há apenas uma implementação DE por ambiente de tempo de execução.  
  
> [!NOTE]
>  Embora as implementações DE separadas para Transact-SQL e JScript, VBScript e JScript compartilham um único DE.  
  
 A DE funciona com o sistema interpretador ou operação para fornecer serviços depuração como avaliação de expressão, pontos de interrupção e controle de execução. Esses serviços são implementados por meio DE interfaces e podem fazer com que o depurador a transição entre os modos operacionais diferentes. Para obter mais informações, consulte [modos operacionais](../../extensibility/debugger/operational-modes.md).  
  
 Criação DE consiste as seguintes etapas:  
  
1.  Registro DE com o Visual Studio  
  
2.  Habilitar um programa a ser depurado  
  
3.  Avaliação de controle e estado de execução  
  
4.  Envio de eventos  
  
5.  Encerramento e desanexação  
  
## <a name="in-this-section"></a>Nesta seção  
 [Registrando um mecanismo de depuração personalizado](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Explica as etapas necessárias para registrar um mecanismo de depuração com o Visual Studio para que ele possa ser usado.  
  
 [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Explica que antes de sua DE pode depurar um programa, você deve primeiro iniciar o DE ou anexá-lo a um programa existente.  
  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Discute por que depurar um aplicativo requer a implementação de recursos de controle de execução.  
  
 [Envio de eventos](../../extensibility/debugger/sending-events.md)  
 Descreve a comunicação entre o depurador e DE como um modelo de evento com base no DCOM.  
  
 [Encerramento e desanexação](../../extensibility/debugger/termination-and-detaching.md)  
 Explica como obter um encerramento normal, o que significa que não há nenhuma interrupção, exceções, erros de tempo de execução ou loops infinitos no aplicativo a ser depurado.  
  
 [Eventos do depurador de chamada](../../extensibility/debugger/calling-debugger-events.md)  
 Documenta a ordem de chamada dos eventos que ocorrem em uma sessão de depuração.  
  
 [Como: Depurar um mecanismo de depuração personalizado](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Explica como depurar um DE personalizado.  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
