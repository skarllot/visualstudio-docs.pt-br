---
title: "M&#233;todos parciais devem ser declarados &#39;Private&#39;, em vez de &#39;&lt; accessModifier &gt;&#39; | Microsoft Docs"
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
  - "vbc31431"
  - "bc31431"
helpviewer_keywords: 
  - "BC31431"
ms.assetid: bbd757f3-7281-4488-8a06-f3b4bcc820dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos parciais devem ser declarados &#39;Private&#39;, em vez de &#39;&lt; accessModifier &gt;&#39;
O modificador de acesso `Private` é necessário nas declarações de método parcial. O exemplo a seguir mostra o uso de `Private` na assinatura do método e sua implementação.  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **ID do erro:** BC31431  
  
### Para corrigir este erro  
  
-   Alterar o modificador de acesso para `Private` nas declarações de assinatura e implementação.  
  
## Consulte também  
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)