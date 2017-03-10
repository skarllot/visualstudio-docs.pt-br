---
title: "&#39;MyBase &#39; deve ser seguido por&#39;.&#39; e um identificador | Microsoft Docs"
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
  - "bc32027"
  - "vbc32027"
helpviewer_keywords: 
  - "BC32027"
ms.assetid: 39e5512c-ef1e-46a3-a96c-277ea24bfee2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MyBase &#39; deve ser seguido por&#39;.&#39; e um identificador
`MyBase` não é uma variável de objeto verdadeira, e não pode aparecer sozinha. Você pode usá\-lo somente para acessar um membro da classe base da instância atual.  
  
 **ID do erro:** BC32027  
  
### Para corrigir este erro  
  
-   Se você pretende acessar o membro, especifique o operador de acesso de membro \(.\) e um membro da classe base após `MyBase`.  
  
-   Se você não pretende acessar um membro, declarar e inicializar uma instância da classe base ou remova a referência à `MyBase`.  
  
## Consulte também  
 [MyBase \- excluir](http://msdn.microsoft.com/pt-br/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)