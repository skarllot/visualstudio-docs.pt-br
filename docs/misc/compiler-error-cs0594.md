---
title: "CS0594 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0594"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0594"
ms.assetid: a3d6bde1-db63-4c5c-a425-8c6a39e00999
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0594 de erro do compilador
Constante de ponto flutuante está fora do intervalo do tipo 'type'  
  
 Um valor foi atribuído a uma variável de ponto flutuante que é muito grande para as variáveis desse tipo de dados. Consulte [tabela de tipos integrais](/dotnet/csharp/language-reference/keywords/integral-types-table) para obter informações sobre o intervalo de valores permitidos em tipos de dados.  
  
 O exemplo a seguir gera CS0594:  
  
```  
// CS0594.cs namespace MyNamespace { public class MyClass { public static void Main() { float f = 6.77777777777E400;   // CS0594, value too large } } }  
```