---
title: "M&#233;todo &#39;&lt; methodname1 &gt;&#39; deve ser declarado como &#39;Private&#39; para implementar o m&#233;todo parcial &#39;&lt; methodname2 &gt;&#39; | Microsoft Docs"
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
  - "vbc31441"
  - "bc31441"
helpviewer_keywords: 
  - "BC31441"
ms.assetid: 4d8d19ad-0c3b-4eba-ada8-2cfa6ae795c4
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todo &#39;&lt; methodname1 &gt;&#39; deve ser declarado como &#39;Private&#39; para implementar o m&#233;todo parcial &#39;&lt; methodname2 &gt;&#39;
A implementação de um método parcial deve ser declarada `Private`. Por exemplo, o código a seguir causa esse erro.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub valueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' Implementation of the partial method, with Private missing, ' causes this error. 'Sub valueChanged() '    MsgBox(Value was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **ID do erro:** BC31441  
  
### Para corrigir este erro  
  
1.  Use o modificador de acesso `Private` na implementação do método parcial, conforme mostrado no exemplo a seguir.  
  
    ```vb#  
    Private Sub valueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub  
    ```  
  
## Consulte também  
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Níveis de acesso no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)