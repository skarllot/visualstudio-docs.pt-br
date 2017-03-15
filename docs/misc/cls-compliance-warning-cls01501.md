---
title: "CLS01501 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01501 de aviso de conformidade CLS
**Restrições varargs não faz parte da CLS**  
  
 Restrições varargs não é parte de subconjunto de linguagem comum \(CLS\).  A única convenção de chamada suportada pelo CLS é que o padrão de convenção de chamada gerenciada.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 A seguinte declaração de função \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS01501:  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 Você pode resolver CLS01501 usando uma matriz de parâmetros.  Consulte [Variable Argument Lists \(...\) \(C\+\+\/CLI\)](/visual-cpp/windows/variable-argument-lists-dot-dot-dot-cpp-cli) para obter mais informações.