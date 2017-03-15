---
title: "Compilador CS3017 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3017"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3017"
ms.assetid: 8e56b2f0-9caf-4c9a-98c2-d3ad0b70e767
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3017 de aviso (n&#237;vel 1)
Não é possível especificar o atributo CLSCompliant em um módulo que difira do atributo CLSCompliant no assembly  
  
 Este aviso ocorre se você tiver um atributo de CLSCompliant de assembly que está em conflito com um atributo CLSCompliant de módulo. Um assembly é compatível com CLS não pode conter módulos que não são compatíveis com CLS. Para resolver esse aviso, verifique se o assembly e atributos do módulo CLSCompliant são ambos true ou ambos os false, ou remova um dos atributos. Para obter mais informações sobre compatibilidade com CLS, consulte [Escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3) e [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemplo  
 O exemplo a seguir gera CS3017:  
  
```  
// CS3017.cs // compile with: /target:module using System; [module: CLSCompliant(true)] [assembly: CLSCompliant(false)]  // CS3017 // Try this line instead: // [assembly: CLSCompliant(true)] class C { static void Main() {} }  
```