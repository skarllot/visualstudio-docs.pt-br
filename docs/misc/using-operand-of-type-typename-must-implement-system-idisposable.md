---
title: "Operando do tipo &#39;&lt; typename &gt;&#39; &#39; using&#39; deve implementar IDisposable | Microsoft Docs"
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
  - "vbc36010"
  - "bc36010"
helpviewer_keywords: 
  - "BC36010"
ms.assetid: ae9ed5d5-68ba-4950-bb7a-61327fa0e7d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operando do tipo &#39;&lt; typename &gt;&#39; &#39; using&#39; deve implementar IDisposable
Um `Using` declaração especifica um recurso de um tipo que implementa o <xref:System.IDisposable> interface.  
  
 A finalidade de um `Using` bloco é garantir o descarte de um recurso do sistema quando você sair do bloco. Para atender a essa finalidade, o recurso deve expor o <xref:System.IDisposable.Dispose%2A> método implementado no <xref:System.IDisposable>.  
  
 **ID do erro:** BC36010  
  
### Para corrigir este erro  
  
-   Remova o recurso da lista de recursos do `Using` instrução, ou substituí\-lo com um recurso que implementa <xref:System.IDisposable>.  
  
## Consulte também  
 <xref:System.IDisposable>   
 [Instrução Using](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Como descartar um recurso do sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)