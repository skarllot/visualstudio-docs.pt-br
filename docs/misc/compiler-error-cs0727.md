---
title: "CS0727 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0727"
ms.assetid: 54bfb87e-d759-4310-a8ab-02dccd06337c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0727 de erro do compilador
Especificador de formato inválida  
  
 Esse erro ocorre no depurador. Quando você digita um nome de variável em uma das janelas do depurador, você pode segui\-lo com uma vírgula e um especificador de formato. Os exemplos são: myInt, h; ou myString, nq. Este erro ocorre quando o compilador é completamente não é possível analisar o que você digitar. Para resolver esse erro, digite novamente o nome da variável, opcionalmente seguido por uma vírgula e um [especificador de formato válido](../debugger/format-specifiers-in-csharp.md).