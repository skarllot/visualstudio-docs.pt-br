---
title: Atividade de GPU (este processo) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 68420704fc10057ae67969d0a8abb550ec71ecbf

---
# <a name="gpu-activity-this-process"></a>Atividade de GPU (este processo)
Os segmentos **Atividade de GPU (este processo)** na exibição Threads na Visualização Simultânea representam o tempo durante o qual a GPU estava processando solicitações em nome do processo atual. Essas solicitações são enviadas à GPU como pacotes de DMA (acesso direto à memória). O tamanho de um segmento representa o tempo durante o qual a GPU estava processando um pacote de DMA em nome do processo atual.  
  
 Quando você seleciona o segmento de atividade de GPU, o relatório na guia **Atual** exibe informações sobre o pacote de DMA que foi processado. Essas informações incluem a quantidade de tempo que o pacote esperou na fila de hardware associada ao mecanismo do DirectX, o processo que enviou o pacote e o tempo necessário para processar o pacote. Um processo diferente do processo atual pode ter enviado fisicamente o pacote de DMA à GPU. A Visualização Simultânea pode detectar quando outro processo enviou trabalho à GPU em nome do processo atual.


<!--HONumber=Feb17_HO4-->


