---
title: "CS1541 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1541"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1541"
ms.assetid: db3350fe-6432-4617-8b4a-64bc6cdf83f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1541 de erro do compilador
Opção de referência inválida: 'symbol' — não é possível fazer referência a diretórios  
  
 O compilador detectou uma tentativa para especificar um diretório em vez de um arquivo específico. Por exemplo, quando você usa o [\/Reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) opção de compilador, você deve especificar um arquivo, ele não é possível especificar um diretório.  
  
 Por exemplo, passar `/reference:c:\` para o compilador poderia gerar CS1541.