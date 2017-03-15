---
title: "&#39;prefix&#39; &#233; um prefixo XML e n&#227;o pode ser usado como uma express&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;prefix&#39; &#233; um prefixo XML e n&#227;o pode ser usado como uma express&#227;o
'prefix' é um prefixo XML e não pode ser usado como uma expressão. Use o operador GetXmlNamespace para criar um objeto de namespace.  
  
 O prefixo para um namespace XML que é importado usando o `Imports` instrução não pode ser usada fora de um literal XML.  
  
 **ID do erro:** BC30114  
  
### Para corrigir este erro  
  
-   Se você precisar fazer referência a parte do namespace XML importado, use o `GetXmlNamespace` operador para recuperar um <xref:System.Xml.Linq.XNamespace> objeto. Use esse objeto em vez do prefixo de namespace XML.  
  
-   Se você estiver usando o prefixo de namespace XML para determinar um literal XML, certifique\-se de que você está usando a sintaxe apropriada para o literal XML.  
  
## Consulte também  
 [Literais XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Instrução Imports \(namespace XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [Operador GetXmlNamespace](/dotnet/visual-basic/language-reference/operators/getxmlnamespace-operator)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)