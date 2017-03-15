---
title: "Cadeia de caracteres de padr&#227;o inv&#225;lido | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cadeia de caracteres de padr&#227;o inv&#225;lido
A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.  
  
### Para corrigir este erro  
  
1.  Examine os caracteres válidos para expressões da lista.  
  
2.  O intervalo padrão, certifique\-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.  
  
3.  O intervalo padrão, certifique\-se de que não haja vários hifens próximos uns dos outros, como em `[a--z]`.  
  
4.  Finalizar intervalos padrão com um colchete de fechamento.  
  
## Consulte também  
 [Operador Like](/dotnet/visual-basic/language-reference/operators/like-operator)