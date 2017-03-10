---
title: "Tipos de dados dos par&#226;metros de tipo no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; typename &gt;&#39; n&#227;o podem ser inferidos a partir destes argumentos | Microsoft Docs"
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
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36646"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados dos par&#226;metros de tipo no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; typename &gt;&#39; n&#227;o podem ser inferidos a partir destes argumentos
Tipos de dados dos parâmetros de tipo no método de extensão '\< methodname \>' definido em '\< typename \>' não podem ser inferidos a partir destes argumentos. Especificar os dados de tipos explicitamente podem corrigir esse erro.  
  
 Foi feita uma tentativa para usar inferência de tipo para determinar o tipo dados \(ou tipos\) do parâmetro de tipo \(ou parâmetros\) ao avaliar uma chamada para um método de extensão genérica. No entanto, o compilador não é capaz de encontrar um tipo de dados para os parâmetros de tipo neste método, e relata o erro.  
  
> [!NOTE]
>  Quando especificar argumentos não é uma opção \(por exemplo, para operadores de consulta em expressões de consulta\), a mensagem de erro aparece sem a segunda frase.  
  
 O código a seguir demonstra o erro.  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **ID do erro:** BC36649 e BC36646  
  
### Para corrigir este erro  
  
-   Você poderá especificar um tipo de dados para o parâmetro de tipo ou os parâmetros em vez de depender de inferência de tipo.  
  
## Consulte também  
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)