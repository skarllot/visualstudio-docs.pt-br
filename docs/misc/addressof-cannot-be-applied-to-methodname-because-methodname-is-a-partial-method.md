---
title: "&#39;AddressOf&#39; n&#227;o pode ser aplicado a &#39;methodname&#39; porque &#39;methodname&#39; &#233; um m&#233;todo parcial | Microsoft Docs"
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
  - "vbc31440"
  - "bc31440"
helpviewer_keywords: 
  - "BC31440"
ms.assetid: 924dbada-3e0a-4004-a3ae-a209b7c3d1fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddressOf&#39; n&#227;o pode ser aplicado a &#39;methodname&#39; porque &#39;methodname&#39; &#233; um m&#233;todo parcial
Um método parcial foi passado para o `AddressOf` operador. Métodos parciais são valores inválidos para o `AddressOf` operador.  
  
 **ID do erro:** BC31440  
  
### Para corrigir este erro  
  
1.  Adicione um método de implementação para o método parcial. O método de implementação é um valor válido para o `AddressOf` operador. O exemplo a seguir mostra uma assinatura de método parcial e sua implementação.  
  
    ```vb#  
    ' Definition of the partial method signature.  
    Partial Private Sub OnNameChanged()  
        ' The body of the signature is empty.  
    End Sub  
  
    ' Implementation of the partial method.  
    Private Sub OnNameChanged()  
        MsgBox("Name was changed to " & Me.Name)  
    End Sub  
    ```  
  
## Consulte também  
 [Operador AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)