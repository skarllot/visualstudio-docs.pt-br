---
title: "O m&#233;todo &#39;&lt; methodname1 &gt;&#39; n&#227;o pode implementar o m&#233;todo parcial &#39;&lt; methodname2 &gt;&#39; porque &#39;&lt; methodname3 &gt;&#39; j&#225; o implementa | Microsoft Docs"
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
  - "vbc31434"
  - "bc31434"
helpviewer_keywords: 
  - "BC31434"
ms.assetid: 61cba19e-db11-4a06-89d6-4244d411588c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O m&#233;todo &#39;&lt; methodname1 &gt;&#39; n&#227;o pode implementar o m&#233;todo parcial &#39;&lt; methodname2 &gt;&#39; porque &#39;&lt; methodname3 &gt;&#39; j&#225; o implementa
O método '\< methodname1 \>' não pode implementar o método parcial '\< methodname2 \>' porque '\< methodname3 \>' já o implementa. Somente um método pode implementar um método parcial.  
  
 Você não pode ter dois métodos parciais que implementam a mesma declaração de método parcial. O código a seguir causa esse erro.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub ValueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' First implementation of the partial method. Private Sub ValueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub ' Second implementation of the partial method causes this error. 'Private Sub ValueChanged() '    Console.WriteLine("Quantity was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **ID do erro:** BC31434  
  
## Consulte também  
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)