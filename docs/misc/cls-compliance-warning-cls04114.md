---
title: "CLS04114 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS04114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04114"
ms.assetid: 84285fbb-ecd1-46e6-9bdb-dc44db40dcc0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS04114 de aviso de conformidade CLS
Atributos devem ser do tipo 'System::Attribute' ou herdar a partir dele  
  
 Para ser compatível com CLS, um atributo personalizado deve herdar de System::Attribute.  Um atributo não herdam de System::Attribute foi aplicado a um delegado.  
  
 Para mais informações sobre o subconjunto de linguagem comum \(CLS\) verificação de compatibilidade, consulte [Assemblies compatíveis com CLS](http://msdn.microsoft.com/pt-br/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 A declaração a seguir \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS04100:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 e, em seguida, um delegado que usa o atributo:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 Fazendo com que o atributo derivar System::Attribute resolve o aviso:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```