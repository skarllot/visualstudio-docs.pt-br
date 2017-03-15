---
title: "O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; para &#39;&lt; genericprocedurename &gt;&#39; n&#227;o pode ser inferido. | Microsoft Docs"
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
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; para &#39;&lt; genericprocedurename &gt;&#39; n&#227;o pode ser inferido.
Um procedimento genérico é chamado sem fornecer uma lista de argumentos de tipo e Inferência de tipos falha para um dos argumentos de tipo.  
  
 Quando você chama um procedimento genérico, você normalmente fornece um argumento de tipo para cada parâmetro de tipo definido pelo procedimento. No entanto, você tem a alternativa de omitir a lista de argumentos de tipo completamente. Quando você fizer isso, o compilador tenta inferir o tipo de cada argumento de tipo do contexto de sua chamada. Para obter mais informações, consulte "Inferência de tipo" em [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 Uma possível causa da falha de inferência de tipo é uma incompatibilidade de classificação entre um parâmetro de tipo e o tipo de chamada. O código a seguir ilustra isso.  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 No código anterior, as duas chamadas para `findLargest` produzir esse erro porque o parâmetro de tipo `t` chama para uma matriz unidimensional, enquanto os argumentos de tipo, o compilador infere as chamadas são um valor escalar \(`testValue`\) e uma matriz bidimensional \(`testMatrix`\).  
  
 **ID do erro:** BC32050  
  
### Para corrigir este erro  
  
-   Verifique se que os tipos dos argumentos normais são tais que a inferência de tipos é consistente com os parâmetros de tipo declarados para o procedimento genérico.  
  
     \- ou \-  
  
-   Chame o procedimento genérico com uma lista de argumentos de tipo completo, para que a inferência de tipo não é necessária.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)