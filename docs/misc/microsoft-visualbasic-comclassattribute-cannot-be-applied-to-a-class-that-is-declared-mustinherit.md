---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; n&#227;o pode ser aplicado a uma classe que &#233; declarada &#39;MustInherit&#39; | Microsoft Docs"
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
  - "BC32508"
  - "vbc32508"
helpviewer_keywords: 
  - "BC32508"
ms.assetid: c8af606d-f448-4703-98df-e594fd511f92
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; n&#227;o pode ser aplicado a uma classe que &#233; declarada &#39;MustInherit&#39;
Uma classe é declarada com o <xref:Microsoft.VisualBasic.ComClassAttribute>, mas sua declaração especifica `MustInherit`.  
  
 Para ser qualificado para interoperabilidade COM, uma classe do .NET Framework deve satisfazer os requisitos a seguir:  
  
-   Ele deve ser `Public`, todos os seus recipientes devem ser `Public`, e ela deve expor pelo menos um `Public` membro.  
  
-   Ele não deve ser *abstrato*, ou seja, ele não deve ser declarado com `MustInherit`.  
  
-   Ele não deve ser genérico ou ser declarado dentro de um tipo de contêiner genérico.  
  
 **ID do erro:** BC32508  
  
### Para corrigir este erro  
  
-   Remover o `MustInherit` palavra\-chave da declaração de classe.  
  
     \- ou \-  
  
-   Se a classe ou o elemento que contém deve ser genérico, remova o <xref:Microsoft.VisualBasic.ComClassAttribute> da declaração de classe. Você não pode expô\-la a COM.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [Interoperabilidade COM](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)