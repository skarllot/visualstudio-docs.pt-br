---
title: "Compilador CS1570 de aviso (n&#237;vel 1) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1570"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1570"
ms.assetid: a121d5c4-8b90-4cda-af5b-6ba8f23b2b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1570 de aviso (n&#237;vel 1)
O comentário XML em 'em construção' mal\-formados XML — 'razão'  
  
 Ao usar [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option), os comentários no código\-fonte devem ser em XML. Qualquer erro com a marcação XML irá gerar CS1570. Por exemplo:  
  
-   Se você estiver passando uma cadeia de caracteres para um **cref**, como em um [\< exceção \>](../Topic/%3Cexception%3E%20\(C%23%20Programming%20Guide\).md) marca, a cadeia de caracteres deve ser colocada entre aspas duplas.  
  
-   Se você estiver usando uma marca, como [\< seealso \>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md), que não tem uma marca de fechamento, você deve especificar uma barra invertida antes do colchete.  
  
-   Se você precisar usar uma maior\- ou menor\-que símbolo no texto da descrição, você precisa para representá\-los com **& gt;** ou **& lt;**.  
  
-   O atributo de arquivo ou caminho em um [\< incluem \>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) marca estava ausente ou incorretamente formado.  
  
 O exemplo a seguir gera CS1570:  
  
```  
// CS1570.cs // compile with: /W:1 namespace ns { // the following line generates CS1570 /// <summary> returns true if < 5 </summary> // try this instead // /// <summary> returns true if <5 </summary> public class MyClass { public static void Main () { } } }  
```