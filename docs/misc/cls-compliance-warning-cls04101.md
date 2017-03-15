---
title: "CLS04101 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS04101"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04101"
ms.assetid: 5ad21eb4-0c6e-4629-bc4a-af274f8a8d90
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS04101 de aviso de conformidade CLS
Atributos devem ser do tipo 'System::Attribute' ou herdar a partir dele  
  
 Certifique\-se de que todos os atributos aplicados aos parâmetros do construtor tem o tipo 'System. Attribute' ou herdarem a partir dele.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 A declaração a seguir \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS04101:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object { .method public specialname rtspecialname instance void  .ctor() cil managed  
```  
  
 Fazendo com que o atributo derivar System::Attribute resolve o aviso:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object { .method public specialname rtspecialname instance void  .ctor() cil managed  
```