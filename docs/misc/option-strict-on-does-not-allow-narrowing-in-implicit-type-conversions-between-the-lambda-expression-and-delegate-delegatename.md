---
title: "Option Strict On n&#227;o permite restringir em convers&#245;es impl&#237;citas de tipo entre a express&#227;o lambda e delegar &#39;&lt; nomedelegado &gt;&#39; | Microsoft Docs"
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
  - "bc36662"
  - "vbc36662"
helpviewer_keywords: 
  - "BC36662"
ms.assetid: 4504497b-56ba-4631-ad7b-59975f7fee04
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n&#227;o permite restringir em convers&#245;es impl&#237;citas de tipo entre a express&#227;o lambda e delegar &#39;&lt; nomedelegado &gt;&#39;
Com `Option Strict` você não pode ter uma conversão de restrição entre o tipo de dados de um parâmetro em um representante e o parâmetro correspondente de uma expressão lambda atribuído a uma variável do tipo delegado. Por exemplo, no código a seguir, delegar `Del` tem um parâmetro do tipo `Integer`.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String  
```  
  
 Portanto, o parâmetro correspondente de qualquer expressão lambda atribuído a uma variável do tipo `Del` pode ser uma `Integer` ou qualquer tipo de dados para o qual há uma conversão de ampliação de `Integer`.  
  
```vb#  
' Valid. Dim example1 As Del = Function(n As Integer) "Valid" Dim example2 As Del = Function(n As Long) "Valid" ' Not valid. Dim example3 As Del = Function(n As Short) "Not Valid"  
```  
  
 **ID do erro:** BC36662  
  
### Para corrigir este erro  
  
-   Altere o tipo de dados do parâmetro em que o representante ou a expressão lambda para que a relação de ampliação necessária exista.  
  
-   Não Especifica tipos de dados de parâmetro na expressão lambda. Tipos serão inferidos dos parâmetros correspondentes no representante.  
  
    ```vb#  
    Dim example4 As Del = Function(n) "Valid"  
    ```  
  
## Consulte também  
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)