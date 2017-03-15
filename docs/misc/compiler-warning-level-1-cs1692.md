---
title: "Compilador CS1692 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1692"
ms.assetid: 1a6d52e1-0ebb-4990-ac0b-36b05a884a19
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1692 de aviso (n&#237;vel 1)
Número inválido  
  
 Um número de diretivas de pré\-processador, como `#pragma` e `#line`, usar números como parâmetros. Um desses números é inválido porque é muito grande, no formato errado, contém caracteres inválidos e assim por diante. Para corrigir esse erro, corrija o número.  
  
## Exemplo  
 O exemplo a seguir gera CS1692.  
  
```  
// CS1692.cs #pragma warning disable a  // CS1692 // Try this instad: // #pragma warning disable 1691 class A { static void Main() { } }  
```