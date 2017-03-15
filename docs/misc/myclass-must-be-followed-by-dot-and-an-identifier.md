---
title: "&#39;MyClass &#39; deve ser seguido por&#39;.&#39; e um identificador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32028"
  - "vbc32028"
helpviewer_keywords: 
  - "BC32028"
ms.assetid: a7e92b54-32b8-4072-9576-632942f05e0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyClass &#39; deve ser seguido por&#39;.&#39; e um identificador
`MyClass` não é uma variável de objeto verdadeira, e não pode aparecer sozinha. Você pode usá\-lo somente para acessar um membro da instância atual como se fosse `NotOverridable` na classe base.  
  
 **ID do erro:** BC32028  
  
### Para corrigir este erro  
  
1.  Se você pretende acessar um membro da classe, especifique o operador de acesso de membro \(`.`\) e um membro da instância atual após `MyClass`.  
  
2.  Se você não pretende acessar um membro de classe, use o `Me` palavra\-chave.  
  
## Consulte também  
 [MyClass \- excluir](http://msdn.microsoft.com/pt-br/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Me](http://msdn.microsoft.com/pt-br/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)