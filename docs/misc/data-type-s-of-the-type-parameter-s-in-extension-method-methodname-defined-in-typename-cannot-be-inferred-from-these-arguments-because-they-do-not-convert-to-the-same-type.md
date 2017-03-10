---
title: "Tipos de dados dos par&#226;metros de tipo no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;typename&#39; n&#227;o podem ser inferidos esses argumentos porque eles n&#227;o s&#227;o convertidos no mesmo tipo | Microsoft Docs"
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
  - "vbc36658"
  - "bc36661"
  - "vbc36661"
  - "bc36658"
helpviewer_keywords: 
  - "BC36661"
  - "BC36658"
ms.assetid: 0bff97fd-cbe9-4433-8192-6498c6fb5d04
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados dos par&#226;metros de tipo no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;typename&#39; n&#227;o podem ser inferidos esses argumentos porque eles n&#227;o s&#227;o convertidos no mesmo tipo
Tipos de dados dos parâmetros de tipo no método de extensão '\< methodname \>' definido em 'typename' não podem ser inferidos a partir destes argumentos porque eles não são convertidos no mesmo tipo. Especificar os dados de tipos explicitamente podem corrigir esse erro.  
  
 Foi feita uma tentativa para usar inferência de tipo para determinar o tipo dados \(ou tipos\) do parâmetro de tipo \(ou parâmetros\) ao avaliar uma chamada para um método de extensão genérica. O compilador não pôde encontrar um tipo de dados que atenda às restrições de todos os argumentos. Portanto, ele relatou este erro.  
  
> [!NOTE]
>  Quando especificar argumentos não é uma opção \(por exemplo, para operadores de consulta em expressões de consulta\), a mensagem de erro aparece sem a segunda frase.  
  
 O código a seguir demonstra o erro.  
  
```vb#  
Option Strict Off Module Module3 Sub Main() Dim c1 As New Class1 '' Not valid. Integer and Date do not convert to the same type. 'c1.targetMethod(19, #3/4/2007#) End Sub <System.Runtime.CompilerServices.Extension()> _ Sub targetMethod(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **ID do erro:** BC36661 e BC36658  
  
### Para corrigir este erro  
  
-   É possível converter um ou mais argumentos explicitamente em um tipo compatível, conforme mostrado no código a seguir:  
  
    ```  
    c1.targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   Você poderá especificar um tipo de dados para o parâmetro de tipo ou os parâmetros para o qual converter os argumentos, conforme mostrado no código a seguir:  
  
    ```  
    c1.targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Funções de conversão do tipo](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Conversões implícitas e explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)