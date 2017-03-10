---
title: "Par&#226;metro &#39;ByRef&#39; &lt; parametername &gt; n&#227;o pode ser usado em uma express&#227;o de consulta | Microsoft Docs"
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
  - "vbc36533"
  - "bc36533"
helpviewer_keywords: 
  - "BC36533"
ms.assetid: 8067ac87-dd6b-4869-87d0-8a4ce272de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metro &#39;ByRef&#39; &lt; parametername &gt; n&#227;o pode ser usado em uma express&#227;o de consulta
Um parâmetro incluído em uma consulta LINQ é um tipo de ponteiro. Parâmetros usados em expressões de consulta não podem ser passados por referência.  
  
 **ID do erro:** BC36533  
  
### Para corrigir este erro  
  
1.  Declare uma nova variável e atribuir o valor da nova variável a uma cópia do valor que é passado por referência. Use a variável copiada na consulta LINQ. Este é um exemplo:  
  
    ```vb#  
    Sub RunQuery(ByVal collection As List(Of Integer), _  
                 ByRef filterValue As Integer)  
        Dim fv = filterValue  
        Dim queryResult = From num In collection _  
                          Where num < fv  
    End Sub  
    ```  
  
### Para corrigir este erro  
  
1.  Substitua o `ByRef` palavra\-chave com o `ByVal` palavra\-chave para o parâmetro usado na consulta.  
  
## Consulte também  
 [Diferenças entre passar um argumento por valor e por referência](/dotnet/visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)