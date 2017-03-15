---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Captura o restante do quadro atual no arquivo de log dos gráficos.  
  
## Sintaxe  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## Comentários  
 Se outra captura está atualmente em progresso\- como uma captura que foi iniciada pela função de `BeginCapture` \- em que a captura está concluída e registrada os gráficos registrar em log como um quadro distinto.  Imediatamente após, o diagnóstico dos gráficos começam a capturar o restante do quadro atual, que também é registrada como um quadro distinto.  A extremidade do quadro atual é marcada por uma chamada para apresentar.  
  
 Para capturar um quadro, você deve preparar seu aplicativo para capturar e registrar para gráficos \- seja, você deve ter [Init](../debugger/init.md) chamado por uma instância da classe de `VsgDbg` antes de chamar `CaptureCurrentFrame`.  
  
## Consulte também  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)