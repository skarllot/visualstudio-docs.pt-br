---
title: "CLS04104 de aviso de conformidade CLS | Microsoft Docs"
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
  - "CLS04104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04104"
ms.assetid: 89a5c080-c7f3-48b5-b2ff-90aa2236c90e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS04104 de aviso de conformidade CLS
Atributos devem ser do tipo 'System::Attribute' ou herdar a partir dele  
  
 Para ser compatível com CLS, um atributo personalizado deve herdar de System::Attribute.  Um atributo não herdam de System::Attribute foi aplicado a uma função de membro.  
  
 A declaração a seguir \(usando a linguagem do assembly MSIL\) mostra o que poderia causar CLS04111:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 e, em seguida, uma função de membro que usa o atributo:  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 00 00 00 00 00 00 )  
```  
  
 Fazendo com que o atributo derivar System::Attribute resolve o aviso:  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```