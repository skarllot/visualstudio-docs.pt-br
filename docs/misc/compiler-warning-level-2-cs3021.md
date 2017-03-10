---
title: "Compilador CS3021 de aviso (n&#237;vel 2) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3021"
ms.assetid: 89f09e4d-65b0-4422-86ea-85c7e05ac29b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3021 de aviso (n&#237;vel 2)
'type' não precisa de um atributo CLSCompliant porque o assembly não tem um atributo CLSCompliant  
  
 Este aviso ocorre se `[CLSCompliant(false)]` aparece em uma classe em um assembly que não tem um nível de assembly CLSCompliant atributo definido como true \(ou seja, a linha `[assembly: CLSCompliant(true)]`\). Uma vez que o assembly é não declarar próprio CLS compatível, não é necessário para qualquer coisa dentro do assembly para declarar incompatíveis, pois ele é considerado incompatível. Para obter mais informações sobre compatibilidade com CLS, consulte [Escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
 Para eliminar esse aviso, remova o atributo ou adicionar o atributo de nível de assembly.  
  
## Exemplo  
 O exemplo a seguir gera CS3021:  
  
```  
// CS3021.cs using System; // Uncomment the following line to declare the assembly CLS Compliant, // and avoid the warning without removing the attribute on the class. //[assembly: CLSCompliant(true)] // Remove the next line to avoid the warning. [CLSCompliant(false)]               // CS3021 public class C { public static void Main() { } }  
```  
  
## Consulte também  
 [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)