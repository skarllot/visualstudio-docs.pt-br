---
title: "O tipo de vari&#225;vel de recurso &#39;Using&#39; n&#227;o pode ser o tipo de matriz | Microsoft Docs"
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
  - "vbc36012"
  - "bc36012"
helpviewer_keywords: 
  - "BC36012"
ms.assetid: f98c54b0-6ede-48b6-aa31-438664c219f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo de vari&#225;vel de recurso &#39;Using&#39; n&#227;o pode ser o tipo de matriz
Um `Using` declaração especifica uma variável de matriz para um recurso.  
  
 O <xref:System.Array> a classe não implementa o <xref:System.IDisposable> interface, para que o `Using` bloco não pode chamar o <xref:System.IDisposable.Dispose%2A> método em um recurso de matriz.  
  
 **ID do erro:** BC36012  
  
### Para corrigir este erro  
  
-   Usar um tipo diferente de recursos de sistema no `Using` bloco.  
  
## Consulte também  
 [Instrução Using](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Como descartar um recurso do sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)   
 [Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/pt-br/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)