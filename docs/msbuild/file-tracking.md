---
title: Acompanhamento de arquivos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 817f6fa3410f66852746702c32d7d724becd7273
ms.lasthandoff: 02/22/2017

---
# <a name="file-tracking"></a>Acompanhamento de arquivos
O acompanhamento de arquivo registra chamadas no sistema de arquivos do Windows para um processo e seus processos filho. Ao chamar as funções listadas abaixo, os programas controlam quando ativar e desativar esse registro e especificar o arquivo de log a ser usado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Para o acompanhamento no contexto atual.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Retomar acompanhamento após uma chamada para [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Definir o número de threads a serem usados para acompanhamento.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Iniciar um novo contexto de acompanhamento.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Iniciar um novo contexto de acompanhamento com uma raiz especificada.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Finalizar acompanhamento e recursos da versão usados.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Suspender temporariamente o acompanhamento.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Gravar os logs de acompanhamento para todos os contextos.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Gravar os logs de acompanhamento para o contexto atual.
