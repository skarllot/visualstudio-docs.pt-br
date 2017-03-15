---
title: "CS0726 de erro do compilador | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0726 de erro do compilador
'especificador de formato ' não é um especificador de formato válido  
  
 Esse erro ocorre no depurador. Quando você digita um nome de variável em uma das janelas do depurador, você pode segui\-lo com uma vírgula e um especificador de formato. Os exemplos são: `myInt, h` ou `myString,nq`. Este erro ocorre quando o compilador não reconhece o [Especificadores de formato em C\#](../debugger/format-specifiers-in-csharp.md).