---
title: "CS0434 de erro do compilador | Microsoft Docs"
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
  - "CS0434"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0434"
ms.assetid: 8f8871fc-a4bb-4a9e-ba19-999f4943001e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0434 de erro do compilador
O namespace Nomenamespace1 na Nomenamespace2 está em conflito com o tipo TypeName1 em NamespaceName3  
  
 Esse erro ocorre quando um tipo importado e um namespace aninhado importado têm o mesmo nome totalmente qualificado. Quando esse nome é referenciado, o compilador é capaz de distinguir entre os dois. Se você pode alterar o código\-fonte importados, você poderá resolver o erro alterando o nome do tipo ou o namespace para que ambos sejam exclusivas dentro do assembly.  
  
 O código a seguir gera erro CS0434.  
  
## Exemplo  
 Esse código cria a primeira cópia do tipo com o mesmo nome totalmente qualificado.  
  
```  
// CS0434_1.cs // compile with: /t:library namespace TypeBindConflicts { namespace NsImpAggPubImp { public class X { } } }  
```  
  
## Exemplo  
 Esse código cria a segunda cópia do tipo com o mesmo nome totalmente qualificado.  
  
```  
// CS0434_2.cs // compile with: /t:library namespace TypeBindConflicts { // Conflicts with another import (import2.cs). public class NsImpAggPubImp { } // Try this instead: // public class UniqueClassName { } }  
```  
  
## Exemplo  
 Esse código faz referência ao tipo com o mesmo nome totalmente qualificado.  
  
```  
// CS0434.cs // compile with: /r:cs0434_1.dll /r:cs0434_2.dll using TypeBindConflicts; public class Test { public TypeBindConflicts.NsImpAggPubImp.X n2 = null; // CS0434 }  
```