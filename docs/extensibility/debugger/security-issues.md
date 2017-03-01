---
title: "Problemas de segurança | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 12
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
ms.sourcegitcommit: 98a4c85118fc836e1f8922a24700036c9d4837cb
ms.openlocfilehash: fcc65d94f8348674110db6cc0a87e0e3020a4683
ms.lasthandoff: 02/22/2017

---
# <a name="security-issues"></a>Problemas de segurança
Para depurar um programa usando o Visual Studio, as únicas permissões necessárias são os mesmos que um desenvolvedor precisa para executar o programa. Isso inclui a depuração remota para a maioria das situações (algumas situações que envolvem a outros serviços, como o serviço de informações da Internet, podem exigir um nível mais alto de permissões).  
  
 Enquanto o Visual Studio é executado, o Gerenciador de depuração do processo (PDM) controla processos de depuração na máquina local. Remotamente, um programa chamado msvsmon.exe é iniciado pelo desenvolvedor para lidar com a depuração remota e disponibilizar o PDM. (Observe que msvsmon.exe não é um serviço e deve ser iniciado manualmente para habilitar a depuração remota no computador). Quando o Visual Studio (ou msvsmon.exe) não está em execução, nenhum processo é rastreado para depuração.  
  
 Isso significa que um desenvolvedor pode depurar programas que início com nenhuma permissão especial. O desenvolvedor pode até mesmo depurar processos iniciados por outra pessoa se outra pessoa for um membro do mesmo grupo de segurança. E para habilitar a depuração remota, é necessário apenas a necessidade de copiar arquivos para o controle remoto da máquina em Iniciar msvsmon.exe (consulte [depuração remota](../../debugger/remote-debugging.md) para obter mais detalhes).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [Gerenciador de depuração do processo](../../extensibility/debugger/process-debug-manager.md)   
 [Depuração remota](../../debugger/remote-debugging.md)
