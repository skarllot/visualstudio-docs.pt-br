---
title: "CLS04113 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS04113"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04113"
ms.assetid: 628f56bf-5f2f-4245-b4fd-02d4605a901c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS04113 de aviso de conformidade CLS
**Atributos devem ser do tipo 'System::Attribute' ou herdar a partir dele**  
  
 Para ser compatível com CLS, um atributo personalizado deve herdar de System::Attribute.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 A declaração a seguir \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS04100:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 Fazendo com que o atributo derivar System::Attribute resolve o aviso:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```