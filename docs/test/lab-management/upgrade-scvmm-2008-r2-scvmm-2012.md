---
title: Atualizar SCVMM 2008 R2 para SCVMM 2012 | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.assetid: 5be92444-c701-43c7-8b2a-77df8e02bc27
caps.latest.revision: 56
ms.author: douge
manager: douge
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: b7874e87ea81bf6b0818b4b9eefba0f86bd2a2e2
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>Atualizar SCVMM 2008 R2 para SCVMM 2012

O Lab Management para Team Foundation Server dá suporte ao SCVMM 2008 R2 e SCVMM 2012. Se você estiver atualizando o Team Foundation Server 2013 para o Team Foundation Server 2015 e pretende atualizar o SCVMM 2008 R2 para o SCVMM 2012, recomendamos que você atualize para o SCVMM 2012 depois de concluir a atualização para o Team Foundation Server 2015. Este tópico descreve como atualizar o SCVMM 2008 R2 para o SCVMM 2012 quando estiver usando o Lab Management no Team Foundation Server 2015.
O Lab Management **não** dá suporte ao SCVMM 2016. 

**Importante:** quando você atualiza o SCVMM, determinadas etapas causarão algum tempo de inatividade para o Team Foundation Server. Você encontrará essas etapas a seguir.

## <a name="upgrading-to-scvmm-2012"></a>Atualizando para o SCVMM 2012

1. Use o instalador do SCVMM 2012 para atualizar o SCVMM 2008 R2 Server para o SCVMM 2012 Server.

1. Atualize os agentes do SCVMM nos compartilhamentos de biblioteca e hosts.

1. Use o Console de Administração do SCVMM para verificar se todos os componentes do SCVMM estão funcionando.

1. Instale o Console de Administração do SCVMM 2012 em todos os computadores da camada de aplicativo do Team Foundation Server.

1. Use o comando **iisreset** para reiniciar o serviço Web do Team Foundation Server. Em seguida, reinicie o agente de trabalho do Team Foundation Server.

   **Cuidado:** esta etapa interromperá os serviços no Team Foundation Server.

1. Atualizar os dados e modelos em cada banco de dados de coleção de projeto para que ele seja compatível com o SCVMM 
   2012.

   Abra um prompt de comando com privilégios elevados no Team Foundation Server e insira o seguinte comando:

   **C:\\Arquivos de Programas\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   Quando você usa o comando **upgradeSCVMM**, o Team Foundation Server cria um novo objeto de modelo em seu servidor do SCVMM para cada projeto de equipe que usa esse modelo. Isso garante que os modelos sejam atualizados para serem compatíveis com o SCVMM 2012 sem perder dados. No entanto, quando os novos modelos são criados, o nome do projeto de equipe é anexado ao nome do modelo.

   **Cuidado:**  
   Se o nome do novo modelo for maior que 64 caracteres, isso causará uma falha no SCVMM. Para resolver esse erro, você deve atribuir um nome mais curto a esses modelos. Se você encontrar outros erros ou avisos quando executar esse comando, consulte a próxima seção para resolver esses erros. Se não encontrar erros ou avisos, a atualização será concluída e você poderá começar a usar ambientes do SCVMM com o Lab Management.

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>Resolvendo erros e avisos ao usar o comando upgradeSCVMM

Depois de usar o comando **upgradeSCVMM**, você deve resolver os erros ou avisos recebidos e executar o comando novamente antes de poder começar a usar o Lab Management. O comando **upgradeSCVMM** gera um arquivo de log que contém informações sobre os erros e avisos que você encontrar. O local do arquivo de log é exibido quando você executa o comando **upgradeSCVMM**.

**Falha do SCVMM:** se você receber um erro relacionado a uma falha do SCVMM, use o histórico de trabalhos do SCVMM para obter informações adicionais sobre o erro. Depois de resolver o erro no SCVMM, execute novamente o comando **upgradeSCVMM**.

## <a name="see-also"></a>Consulte também

* [Alterar as configurações do Lab Management existentes](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)

