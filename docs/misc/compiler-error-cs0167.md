---
title: "CS0167 de erro do compilador | Microsoft Docs"
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
  - "CS0167"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0167"
ms.assetid: e6901b40-11a0-422c-9ea3-3b25c0ad7791
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0167 de erro do compilador
O delegate 'delegate' não foi encontrado no método Invoke  
  
 Importado e usado um programa gerenciado \(um que usa o .NET Framework common language runtime\) que foi criado com outro compilador. Esse compilador permitido um malformados [Delegar](/dotnet/csharp/language-reference/keywords/delegate). Portanto, o `Invoke` método não estava disponível. Para obter mais informações, consulte [Delegados](/dotnet/csharp/programming-guide/delegates/index).