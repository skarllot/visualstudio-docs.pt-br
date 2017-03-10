---
title: "Compilador CS3016 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3016"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3016"
ms.assetid: b2ae721d-13ab-4e9d-a288-741d7825defe
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3016 de aviso (n&#237;vel 1)
Matrizes como argumentos de atributo não é compatível com CLS  
  
 Não é compatível com o Common Language Specification \(CLS\) para passar uma matriz a um atributo. Para obter mais informações sobre compatibilidade com CLS, consulte [Escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3) e [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemplo  
 O exemplo a seguir gera CS3016:  
  
```  
// CS3016.cs using System; [assembly : CLSCompliant(true)] [C(new int[] {1, 2})]   // CS3016 // try the following line instead // [C()] class C : Attribute { public C() { } public C(int[] a) { } public static void Main () { } }  
```