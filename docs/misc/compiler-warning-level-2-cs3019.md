---
title: "Compilador CS3019 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS3019"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3019"
ms.assetid: b41117cf-8956-4989-93fd-9903812e2d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3019 de aviso (n&#237;vel 2)
Verificação de compatibilidade com CLS não será ser executada em 'type' porque ele não é visível fora desse assembly.  
  
 Este aviso ocorre quando um tipo ou um membro que tem o <xref:System.CLSCompliantAttribute> atributo não estiver visível no outro assembly. Para resolver esse erro, remova o atributo em classes ou membros que não são visíveis a partir de outro assembly ou tornar o tipo ou membros visíveis. Para obter mais informações sobre compatibilidade com CLS, consulte [\< PAVE OVER \> escrevendo compatível com CLS código](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3).  
  
## Exemplo  
 O exemplo a seguir gera CS3019:  
  
```  
// CS3019.cs // compile with: /W:2 using System; [assembly: CLSCompliant(true)] // To fix the error, remove the next line [CLSCompliant(true)]  // CS3019 class C { [CLSCompliant(false)]  // CS3019 void Foo() { } static void Main() { } }  
```  
  
## Consulte também  
 [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)