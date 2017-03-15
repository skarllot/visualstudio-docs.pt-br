---
title: "&#39;&lt; construtor &gt;&#39; no designer gerado pelo tipo &#39;&lt; type &gt;&#39; deve chamar o m&#233;todo InitializeComponent | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40054"
  - "bc40054"
helpviewer_keywords: 
  - "BC40054"
ms.assetid: beac93b0-d427-4df6-9582-fd69c7a53673
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; construtor &gt;&#39; no designer gerado pelo tipo &#39;&lt; type &gt;&#39; deve chamar o m&#233;todo InitializeComponent
Um construtor em um tipo gerado pelo designer chama o tipo `InitializeComponent` método.  
  
 Cada construtor em um tipo gerado pelo designer deve chamar o tipo `InitializeComponent` método.  
  
 **ID do erro:** BC40054  
  
### Para corrigir este erro  
  
-   Adicione uma chamada para o `InitializeComponent` método no construtor.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute>   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)