---
title: "Tipos de dados dos par&#226;metros de tipo no m&#233;todo &#39;&lt; methodname &gt;&#39; n&#227;o podem ser inferidos a partir destes argumentos | Microsoft Docs"
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
  - "vbc36648"
  - "bc36645"
  - "bc36648"
  - "vbc36645"
helpviewer_keywords: 
  - "BC36648"
  - "BC36645"
ms.assetid: cc8c67bb-6cbb-4d7c-ba26-fe1d38908434
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados dos par&#226;metros de tipo no m&#233;todo &#39;&lt; methodname &gt;&#39; n&#227;o podem ser inferidos a partir destes argumentos
Tipos de dados dos parâmetros de tipo no método '\< methodname \>' não podem ser inferidos a partir destes argumentos. Especificar os dados de tipos explicitamente podem corrigir esse erro.  
  
 Foi feita uma tentativa para usar inferência de tipo para determinar o tipo dados \(ou tipos\) do parâmetro de tipo \(ou parâmetros\) ao avaliar uma chamada para um procedimento genérico. No entanto, o compilador não é capaz de encontrar um tipo de dados para os parâmetros de tipo neste método, e relata o erro.  
  
> [!NOTE]
>  Quando especificar argumentos não é uma opção \(por exemplo, para operadores de consulta em expressões de consulta\), a mensagem de erro aparece sem a segunda frase.  
  
 Por exemplo, o código a seguir demonstra o erro.  
  
```vb#  
Module Module1 Sub Main() '' Not valid. 'GenericMethod("Hello", "World") End Sub Sub GenericMethod(Of T)(ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface  
```  
  
 **ID do erro:** BC36648 e BC36645  
  
### Para corrigir este erro  
  
-   Você poderá especificar um tipo de dados para o parâmetro de tipo ou os parâmetros em vez de depender de inferência de tipo.  
  
## Consulte também  
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)