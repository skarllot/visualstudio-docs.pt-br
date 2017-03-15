---
title: "CS0424 de erro do compilador | Microsoft Docs"
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
  - "CS0424"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0424"
ms.assetid: 09ae482c-255a-4f99-8dc8-ba31c3ea8c71
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0424 de erro do compilador
'class': uma classe com o atributo ComImport não pode especificar uma classe base  
  
 Especificando o <xref:System.Runtime.InteropServices.ComImportAttribute> atributo implica que a implementação da classe deve ser importada de um módulo COM. Não são permitidos métodos adicionais ou campos herdados da classe base a ser adicionado à implementação definida no módulo de COM.  
  
 O exemplo a seguir gera CS0424:  
  
```  
// CS0424.cs // compile with: /target:library using System.Runtime.InteropServices; public class A {} [ ComImport, Guid("7ab770c7-0e23-4d7a-8aa2-19bfad479829") ] class B : A {}   // CS0424 error  
```