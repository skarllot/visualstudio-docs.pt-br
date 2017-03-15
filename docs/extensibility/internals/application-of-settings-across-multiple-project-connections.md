---
title: "Aplicação de configurações por várias conexões de projeto | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
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
ms.openlocfilehash: 130255846ed7b96ba5e704947da2f9f27346c430
ms.lasthandoff: 02/22/2017

---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicação de configurações por várias conexões de projeto
Um plug-in de controle de origem criados usando o código-fonte controle plug-in API 1.2, pode usar uma operação em lotes para executar a mesma operação de controle de origem em vários contextos de conexão ou de vários projetos. Lotes podem ser usados para eliminar redundantes, caixas de diálogo a experiência do usuário por projeto.  
  
 Se um usuário seleciona vários itens que pertencem a mais de uma conexão em um plug-in de controle de origem criado 1.1 de API de plug-in a origem, (por exemplo, dois projetos para Web em máquinas diferentes de compartilhamento de arquivos) e verifica-os, o usuário vê repetidamente a mesma caixa de diálogo. Isso acontecerá mesmo se o usuário clica o **aplicar a todos** caixa na caixa de diálogo de seleção porque o IDE redefine seu estado para cada contexto de conexão.  
  
## <a name="new-capability-flag"></a>Novo sinalizador de recurso  
 `SccBeginBatch`Função define o `SCC_CAP_BATCH` sinalizador para indicar que uma operação em lote está em andamento  
  
## <a name="new-functions"></a>Novas funções  
 As novas funções a seguir oferece suporte à operação de lote:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 O `SCCBeginBatch` um grupo de operações de controle do código-fonte da função é iniciada. `SccEndBatch`Fecha o grupo. Os grupos não podem ser aninhados.  
  
## <a name="see-also"></a>Consulte também  
 [Novidades na origem controle plug-in API versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
