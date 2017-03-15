---
title: "CLS01506 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS01506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01506"
ms.assetid: 030f1b81-1159-4057-9fee-8721a419a5d6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS01506 de aviso de conformidade CLS
Restrições varargs não faz parte da CLS  
  
 Restrições varargs não é parte de subconjunto de linguagem comum \(CLS\).  A única convenção de chamada suportada pelo CLS é que o padrão de convenção de chamada gerenciada.  
  
 Para mais informações sobre conformidade verificação CLS, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 A seguinte declaração de função \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS01506:  
  
```  
.method public instance vararg void  Method1() cil managed  
```  
  
 Removendo o **vararg** palavra\-chave, você pode resolver este aviso:  
  
```  
.method public instance void  Method1() cil managed  
```