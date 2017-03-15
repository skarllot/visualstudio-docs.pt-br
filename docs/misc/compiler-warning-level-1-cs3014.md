---
title: "Compilador CS3014 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3014"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3014"
ms.assetid: 6825b42f-1820-4265-b8d8-9b3387d7c130
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3014 de aviso (n&#237;vel 1)
'member' não precisa de um atributo CLSCompliant porque o assembly não tem um atributo CLSCompliant  
  
 Em um arquivo de código fonte em conformidade com a Common Language Specification \(CLS\) não foi especificada, uma construção no arquivo foi marcada como sendo compatível com CLS. Isso não é permitido. Para resolver esse aviso, adicione um atributo de compatível com assembly nível CLS para o arquivo \(no exemplo a seguir, remova a linha que contém o atributo de nível de assembly\). Para obter mais informações sobre compatibilidade CLS, consulte [Escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3) e [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemplo  
 O exemplo a seguir gera CS3014:  
  
```  
// CS3014.cs using System; // [assembly:CLSCompliant(true)] public class I { [CLSCompliant(true)]   // CS3014 public void M() { } public static void Main() { } }  
```