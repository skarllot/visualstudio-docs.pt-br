---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Termina um intervalo de captura que é iniciado com `BeginCapture`.  
  
## Sintaxe  
  
```cpp  
void EndCapture();  
```  
  
## Comentários  
 Um intervalo de captura medidas normalmente um subconjunto de um quadro, como quando você deseja capturar informações dos gráficos apenas em um determinado tipo de chamada de descompasso.  Se o intervalo de captura abrange uma chamada para apresentar a seguir, dois peças de informações dos gráficos são capturados.  O primeiro quadro ultrapassar o intervalo entre a chamada a `BeginCapture` e a chamada para apresentar; o segundo quadro ultrapassar o intervalo entre o primeiro evento de Direct3D depois que a chamada para apresentar e chame para `EndCapture`.  
  
 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e registrar para gráficos \- seja, você deve ter [Init](../debugger/init.md) chamado por uma instância da classe de `VsgDbg` antes de chamar `BeginCapture` ou `EndCapture`.  
  
## Consulte também  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)