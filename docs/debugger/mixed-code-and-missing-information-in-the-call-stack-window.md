---
title: "C&#243;digo misto e informa&#231;&#245;es ausentes na janela Pilha de Chamadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "janela de Pilha de Chamadas, depuração de modo misto"
  - "janela de Pilha de Chamadas, solucionando problemas"
  - "pilhas de chamadas gerenciadas"
  - "código gerenciado, depurando"
  - "depuração de modo misto, pilha de chamadas"
  - "quadros nativos"
  - "depurando, de código gerenciado"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;digo misto e informa&#231;&#245;es ausentes na janela Pilha de Chamadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Devido às diferenças entre as pilhas de chamadas para código gerenciado e nativo, o depurador nem sempre pode mostrar a pilha de chamadas completa quando os tipos de código são misturados.  Quando o código nativo chama o código gerenciado, você pode observar as seguintes discrepâncias na janela **Pilha de Chamadas**:  
  
-   O quadro nativo imediatamente acima do código gerenciado pode estar ausente da janela **Pilha de Chamadas**.  Para obter mais informações, consulte [Como sair do código gerenciado quando quadros nativos não forem encontrados na janela Pilha de Chamadas](../Topic/How%20to:%20Step%20out%20of%20Managed%20Code%20when%20Native%20Frames%20are%20Missing%20from%20the%20Call%20Stack%20Window.md).  
  
-   Para os aplicativos de modo misto iniciados fora do depurador, a janela **Pilha de Chamadas** pode exibir somente o código gerenciado e nenhum dos quadros nativos estarão visíveis.  
  
 Ambos os casos são razoavelmente incomuns.  Na maioria das chamadas nativas para o código gerenciado, as pilhas de chamadas são exibidas corretamente.  
  
## Consulte também  
 [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md)