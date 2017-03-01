---
title: Habilitar um programa a ser depurado | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
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
ms.openlocfilehash: 66daff038c7556a693964d5dabc4de054990d791
ms.lasthandoff: 02/22/2017

---
# <a name="enabling-a-program-to-be-debugged"></a>Habilitar um programa a ser depurado
Antes do mecanismo de depuração (DE) pode depurar um programa, você deve primeiro iniciar DE ou anexá-lo a um programa existente.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Obtendo uma porta](../../extensibility/debugger/getting-a-port.md)  
 Discute como obter uma porta como a primeira etapa para habilitar um programa a ser depurado.  
  
 [Registrando o programa](../../extensibility/debugger/registering-the-program.md)  
 Explica a próxima etapa para habilitar um programa a ser depurado: registrá-lo com a porta. Depois de registrado, o programa pode ser depurado, o processo de anexar ou depuração just-in-time (JIT).  
  
 [Anexando ao programa](../../extensibility/debugger/attaching-to-the-program.md)  
 Explica a próxima etapa: anexando o depurador para o programa.  
  
 [Anexando com base no lançamento](../../extensibility/debugger/launch-based-attachment.md)  
 Descreve o anexo baseado no lançamento para um programa, que é automático durante a inicialização, o SDM.  
  
 [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)  
 Percorre os eventos necessários durante a criação de um mecanismo de depuração (DE) e anexá-lo a um programa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define um mecanismo de depuração (DE) e descreve os serviços implementados por meio DE interfaces e como eles podem causar o depurador a transição entre os diferentes modos operacionais.
