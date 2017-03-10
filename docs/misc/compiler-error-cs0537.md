---
title: "CS0537 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0537"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0537"
ms.assetid: 6c832a5f-47dc-4f60-aed8-69ac328af44b
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0537 de erro do compilador
A classe System. Object não pode ter uma classe base ou implementar uma interface  
  
 CS0537 ocorre durante a recriação do <xref:System> bibliotecas de classe e onde <xref:System.Object> deriva de outra classe. Você é muito improvável que encontrar esse erro. Se você fizer isso, não derivar <xref:System.Object> de uma classe ou interface: é a raiz de toda a hierarquia de classe do .NET Framework e, como tal, não é derivado de qualquer outra coisa.