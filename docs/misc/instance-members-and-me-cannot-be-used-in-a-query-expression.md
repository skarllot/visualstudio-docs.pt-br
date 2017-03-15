---
title: "Membros de inst&#226;ncia e &#39;Me&#39; n&#227;o pode ser usado em uma express&#227;o de consulta | Microsoft Docs"
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
  - "vbc36535"
  - "bc36535"
helpviewer_keywords: 
  - "BC36535"
ms.assetid: afb5281b-70a7-48c7-a46d-39522b96b1ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membros de inst&#226;ncia e &#39;Me&#39; n&#227;o pode ser usado em uma express&#227;o de consulta
Uma consulta LINQ em um `Structure` inclui uma referência a `Me` ou a um membro de instância da estrutura. As referências a `Me` ou membros de instância não são permitidos em expressões de consulta dentro de um `Structure`.  
  
 **ID do erro:** BC36535  
  
### Para corrigir este erro  
  
1.  Criar uma cópia de membro de instância ou o valor retornado por referência a `Me` e usar a cópia na expressão de consulta, conforme mostrado no exemplo a seguir.  
  
    ```vb#  
    Structure SampleStructure Public SearchValue As Integer Public Sub SetSearchValue(ByVal number As Integer) SearchValue = number End Sub Public Sub GetData() Dim sv = SearchValue Dim SampleData = New Integer() {1, 2, 3, 4} Dim query = From number In SampleData _ Where number < sv End Sub End Structure  
    ```  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Me](http://msdn.microsoft.com/pt-br/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)