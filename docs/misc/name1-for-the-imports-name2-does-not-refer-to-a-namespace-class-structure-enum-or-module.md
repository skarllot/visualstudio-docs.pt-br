---
title: "&#39;&lt; Nome1 &gt;&#39; para Imports &#39;&lt; nome2 &gt;&#39; n&#227;o faz refer&#234;ncia a um Namespace, classe, estrutura, Enum ou m&#243;dulo | Microsoft Docs"
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
  - "vbc30467"
  - "bc30467"
helpviewer_keywords: 
  - "BC30467"
ms.assetid: a4b8a23b-ba1b-44f7-9584-258dd2607581
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; Nome1 &gt;&#39; para Imports &#39;&lt; nome2 &gt;&#39; n&#227;o faz refer&#234;ncia a um Namespace, classe, estrutura, Enum ou m&#243;dulo
Você tentou usar o `Imports` instrução em algo que não seja um `Namespace`, `Class`, `Structure`, `Enum`, ou `Module`. O `Imports` instrução importa nomes de namespace de projetos e assemblies referenciados, ou importa os nomes de namespaces definidos dentro do mesmo projeto como o módulo no qual a instrução aparece.  
  
 **ID do erro:** BC30467  
  
### Para corrigir este erro  
  
-   Verifique a entidade que você está tentando importar e verifique se ela é válida para uso com um `Imports` instrução.  
  
## Consulte também  
 [Instrução Imports \(tipo e namespace .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Referências e a instrução Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)