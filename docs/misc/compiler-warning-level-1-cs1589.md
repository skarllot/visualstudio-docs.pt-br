---
title: "Compilador CS1589 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1589"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1589"
ms.assetid: bdc47124-93ae-4c6a-81b2-dde8ec4d0ab1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1589 de aviso (n&#237;vel 1)
Não é possível incluir o fragmento XML fragmento do arquivo 'arquivo' \- motivo  
  
 A sintaxe \(*fragmento*\) de um [\< incluem \>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) marca, que consultou um arquivo \(`file`\), estava incorreto especificado ***motivo***.  
  
 Uma linha malformada será colocada no arquivo XML gerado.  
  
 O exemplo a seguir gera CS1589:  
  
```  
// CS1589.cs // compile with: /W:1 /doc:CS1589_out.xml /// <include file='CS1589.doc' path='MyDocs/MyMembers[@name="test"]/' />   // CS1589 // try the following line instead // /// <include file='CS1589.doc' path='MyDocs/MyMembers[@name="test"]/*' /> class Test { public static void Main() { } }  
```