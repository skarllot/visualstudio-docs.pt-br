---
title: "Exibição de processo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
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
ms.openlocfilehash: a1f55111b5fcc8c36a5bfc8f86d25354fa89d8b8
ms.lasthandoff: 02/22/2017

---
# <a name="process-view"></a>Exibição de processo
A exibição do processo exibe dados de criação de perfil para os processos e threads executados durante o processo de criação de perfil.  
  
 Os processos são listados por nome. Os threads são listados como nós filhos do processo que os criou. Os threads são nomeados pela função que iniciou o thread ou pelo rótulo **[ntdll.dll]** quando não há símbolos disponíveis.  
  
 Clique com o botão direito do mouse na exibição e, em seguida, selecione **Adicionar/Remover Colunas** para adicionar ou remover colunas. Ou clique no nome da coluna para classificar os dados. Para obter mais informações, consulte [Como personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md).  
  
 As colunas da exibição de processo são as mesmas usadas pelos gerados pelos métodos de amostragem e instrumentação e pelos dados que incluem dados de memória do .NET. A tabela a seguir descreve os valores da coluna.  
  
|Column|Descrição|  
|------------|-----------------|  
|**ID exclusiva**|Um identificador gerado pelo criador de perfil que é exclusivo ao processo ou thread.|  
|**ID**|O identificador do processo ou thread gerado pelo sistema.|  
|**Nome**|O nome do processo ou thread.|  
|**Hora de início**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o início do processo ou thread.|  
|**Hora de término**|O número de milissegundos ou ciclos de processador desde o início da criação de perfil até o fim do processo ou thread.|  
  
## <a name="see-also"></a>Consulte também  
 [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)   
 [Exibições de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)   
 [Exibições de dados da memória do .NET](../profiling/dotnet-memory-data-views.md)
