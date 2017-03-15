---
title: "CS2020 de erro do compilador | Microsoft Docs"
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
  - "CS2020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2020"
ms.assetid: b2db7a05-5965-4a9b-86c3-0c4792b29a6c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS2020 de erro do compilador
Somente o primeiro conjunto de arquivos de entrada pode criar um destino diferente de 'module'  
  
 Em uma compilação de várias saída, o primeiro arquivo de saída deve ser criado com [\/target: exe](../Topic/-target:exe%20\(C%23%20Compiler%20Options\).md), [\/target: winexe](../Topic/-target:winexe%20\(C%23%20Compiler%20Options\).md), ou [\/target: Library](../Topic/-target:library%20\(C%23%20Compiler%20Options\).md). Os arquivos de saída subsequentes devem ser criados com [\/target: Module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md).