---
title: "Nome do par&#226;metro &#39;&lt; parametername1 &gt;&#39; n&#227;o coincide com o nome do par&#226;metro correspondente, &#39;&lt; parametername2 &gt;&#39;, definido na declara&#231;&#227;o de m&#233;todo parcial &#39;&lt; methodname &gt;&#39; | Microsoft Docs"
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
  - "vbc31442"
  - "bc31442"
helpviewer_keywords: 
  - "BC31442"
ms.assetid: 7f097bb2-071a-42ec-b7af-40da04f602f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nome do par&#226;metro &#39;&lt; parametername1 &gt;&#39; n&#227;o coincide com o nome do par&#226;metro correspondente, &#39;&lt; parametername2 &gt;&#39;, definido na declara&#231;&#227;o de m&#233;todo parcial &#39;&lt; methodname &gt;&#39;
Quando os parâmetros são fornecidos para a declaração e a implementação de um método parcial, os nomes dos parâmetros correspondentes devem ser os mesmos. Por exemplo, o código a seguir causa esse erro.  
  
```vb#  
Partial Class Product  
  
    ' Declaration of the partial method.  
    Partial Private Sub valueChanged(ByVal newVal As Integer)  
    End Sub  
End Class  
```  
  
```vb#  
Partial Class Product  
  
    ' Implementation of the partial method. This error is  
    ' reported for parameter val.  
    ' Private Sub valueChanged(ByVal val As Integer)  
    '     MsgBox(Value was changed to " & Me.Quantity)  
    ' End Sub  
  
End Class  
```  
  
 **ID do erro:** BC31442  
  
### Para corrigir este erro  
  
1.  Altere o nome do parâmetro ou nomes na declaração ou na implementação para que os parâmetros correspondentes tenham o mesmo nome.  
  
## Consulte também  
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)