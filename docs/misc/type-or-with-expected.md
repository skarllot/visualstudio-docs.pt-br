---
title: "Tipo ou &#39;With&#39; esperado | Microsoft Docs"
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
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo ou &#39;With&#39; esperado
Quando você declara uma instância de uma classe, o `New` palavra\-chave deve ser seguido por um nome de tipo ou por `With`. Por exemplo, cada instrução a seguir declara `client` deve ser uma instância de `Customer` classe. O nome do tipo `Customer` segue `New`.  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 Começando com [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)], você pode declarar um objeto para ser uma instância de um tipo anônimo, nesse caso você não especificar um tipo de dados. Em declarações de tipo anônimo, a palavra\-chave `With` segue `New`.  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **ID do erro:** BC30988  
  
### Para corrigir este erro  
  
-   Altere a declaração para que `With` ou um nome de tipo segue `New`.  
  
## Consulte também  
 [Tipos anônimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Instruções de NotInBuild:Declaration no Visual Basic](http://msdn.microsoft.com/pt-br/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)