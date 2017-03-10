---
title: "Depurando F# | Microsoft Docs"
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
helpviewer_keywords: 
  - "Depurando [F#]"
  - "F#, depuração"
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando F# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A depuração de F\# é semelhante à depuração de qualquer linguagem gerenciada, com algumas exceções:  
  
-   A janela **Autos** não exibe as variáveis de F\#.  
  
-   Não há suporte para Editar e Continuar em F\#.  As edições ao código F\# durante uma sessão de depuração são possíveis, mas devem ser evitadas.  Como as alterações de código não são aplicadas durante a sessão de depuração, a edição do código F\# durante a depuração causará uma incompatibilidade entre o código\-fonte e o código que está sendo depurado.  
  
-   O depurador não reconhece expressões de F\#.  Para inserir uma expressão em uma janela ou uma caixa de diálogo do depurador durante a depuração de F\#, você deve traduzir a expressão para a sintaxe do C\#.  Quando você traduzir uma expressão F\# em C\#, lembre\-se de que o C\# usa \=\= como o operador de comparação para igualdade, enquanto o F\# usa o \= simples.  
  
## Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)