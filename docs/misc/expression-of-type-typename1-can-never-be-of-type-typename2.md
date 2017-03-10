---
title: "Express&#227;o do tipo &#39;&lt; typename1 &gt;&#39; nunca pode ser do tipo &#39;&lt; typename2 &gt;&#39; | Microsoft Docs"
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
  - "vbc31430"
  - "bc31430"
helpviewer_keywords: 
  - "BC31430"
ms.assetid: 1d527033-3f6f-4945-b1d3-5ef59a1e1b53
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o do tipo &#39;&lt; typename1 &gt;&#39; nunca pode ser do tipo &#39;&lt; typename2 &gt;&#39;
A `TypeOf`...`Is` testa uma variável de referência de objeto para um tipo de dados que ela não pode conter.  
  
 Em alguns casos, o compilador pode determinar que um `TypeOf`…`Is` somente poderá falhar, por exemplo, se não houver nenhuma relação de herança entre duas classes.  
  
 O código a seguir pode gerar esse erro.  
  
 `Dim refVar as System.Windows.Forms.Form`  
  
 `If TypeOf refVar Is System.Array`  
  
 `End If`  
  
 Como <xref:System.Windows.Forms.Form> e <xref:System.Array> são tipos totalmente não relacionados, o compilador pode determinar que o `TypeOf`...`Is` retorna `False` para qualquer valor de `refVar`.  
  
 **ID do erro:** BC31430  
  
### Para corrigir este erro  
  
-   Teste a variável para um tipo de dados realista, ou remova o `TypeOf`...`Is` testar completamente.  
  
## Consulte também  
 [Operador TypeOf](/dotnet/visual-basic/language-reference/operators/typeof-operator)   
 [Como determinar a que tipo uma variável de objeto se refere](../Topic/How%20to:%20Determine%20What%20Type%20an%20Object%20Variable%20Refers%20To%20\(Visual%20Basic\).md)