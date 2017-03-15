---
title: "CS0268 de erro do compilador | Microsoft Docs"
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
  - "CS0268"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0268"
ms.assetid: a4faca71-8b4a-4f22-a89e-59d92ced48cb
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0268 de erro do compilador
Tipo importado 'type' é inválido. Ele contém uma dependência de classe base circular.  
  
 Esse erro ocorre se um tipo importado de outra linguagem tem uma dependência circular de classe base. Um tipo não pode ser usado em um programa c\#. Para resolver esse erro, verifique os tipos importados de outras linguagens em módulos ou assemblies referenciados.