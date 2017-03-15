---
title: "&#39;Microsoft.VisualBasic.ComClassAttribute&#39; n&#227;o pode ser aplicado a uma classe gen&#233;rica ou aninhadas dentro de um tipo gen&#233;rico | Microsoft Docs"
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
  - "vbc31527"
  - "bc31527"
helpviewer_keywords: 
  - "BC31527"
ms.assetid: ea125bff-d020-4933-b277-6e24943eea88
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Microsoft.VisualBasic.ComClassAttribute&#39; n&#227;o pode ser aplicado a uma classe gen&#233;rica ou aninhadas dentro de um tipo gen&#233;rico
Uma classe é declarada com <xref:Microsoft.VisualBasic.ComClassAttribute>, mas é genérica ou contidas em uma classe genérica ou estrutura.  
  
 Para ser qualificado para interoperabilidade COM, uma classe do .NET Framework deve satisfazer os requisitos a seguir:  
  
-   Ele deve ser `Public`, todos os seus recipientes devem ser `Public`, e ela deve expor pelo menos um `Public` membro.  
  
-   Ele não deve ser *abstrato*, ou seja, ele não deve ser declarado com `MustInherit`.  
  
-   Ele não deve ser genérico ou ser declarado dentro de um tipo de contêiner genérico.  
  
 **ID do erro:** BC31527  
  
### Para corrigir este erro  
  
-   Altere a declaração da classe para que ele não seja genérico e verifique se que o elemento que contém não é genérico.  
  
     \- ou \-  
  
-   Se a classe ou o elemento que contém deve ser genérico, remova <xref:Microsoft.VisualBasic.ComClassAttribute> da declaração de classe. Você não pode expô\-la a COM.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [Interoperabilidade COM](/dotnet/visual-basic/programming-guide/com-interop/index)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)