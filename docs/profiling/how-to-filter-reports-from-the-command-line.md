---
title: "Como filtrar relatórios da linha de comando | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
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
ms.openlocfilehash: 589354ceb92c3822072ecb95126d343292cb72f8
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-filter-reports-from-the-command-line"></a>Como filtrar relatórios a partir da linha de comando
Ao usar as opções para o comando **VSPerfReport**, você pode filtrar relatórios para um segmento de tempo específico do arquivo de dados de criação de perfil ou restringir os dados a um ou mais processos ou threads. Para obter mais informações sobre esse comando, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opções|Descrição|  
|-------------|-----------------|  
|**StartTime:**[*Value*]|Mostrar somente dados coletados após o valor (em milésimos de segundos.)|  
|**EndTime:**[*Value*]|Mostrar apenas dados coletados antes do valor (em milésimos de segundos.)|  
|**FilterFile:** `VSPFFile`|Especifica o local de um arquivo de filtro que foi gerado da janela **Relatório de desempenho do Visual Studio**.|  
|**MsFilter:**[*StartTime,Duration*]|Mostrar somente os dados de `StartTime` até a duração de `Duration` (em milésimos de segundos).|  
|**Process:**[*Pid*]|Mostrar somente os dados do processo especificado.|  
|**Thread:**[*ThreadID*]|Mostrar somente os dados do thread especificado.|  
|**Thread:**[*ThreadID,ProcessID*]|Mostrar somente os dados do thread especificado associados ao processo especificado.|
