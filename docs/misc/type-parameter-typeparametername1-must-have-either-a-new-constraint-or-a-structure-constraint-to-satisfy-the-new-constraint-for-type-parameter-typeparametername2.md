---
title: "O par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; deve ter uma restri&#231;&#227;o &#39;New&#39; ou &#39; Structure &#39; para satisfazer &#224; restri&#231;&#227;o &#39;New&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername2 &gt;&#39; | Microsoft Docs"
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
  - "vbc32084"
  - "BC32084"
helpviewer_keywords: 
  - "BC32084"
ms.assetid: a7ff58d3-8c67-40e4-9fd8-92cc00524c22
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; deve ter uma restri&#231;&#227;o &#39;New&#39; ou &#39; Structure &#39; para satisfazer &#224; restri&#231;&#227;o &#39;New&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername2 &gt;&#39;
Uma instrução constrói um tipo genérico passando um parâmetro de tipo que não é restrito para satisfazer uma `New` restrição.  
  
 O `New` restrição significa que o argumento de tipo fornecido para esse parâmetro de tipo deve expor um construtor sem parâmetros acessível para o código que cria objetos a partir dele. Todos os tipos de valor têm construtores sem parâmetros, mas nem todos os tipos de referência. Portanto o `Structure` restrições atendem a `New` restrição, mas o `Class` restrição ou um nome de classe ou interface, não.  
  
 As instruções a seguir podem gerar esse erro.  
  
```  
Public Class c1(Of t As New) End Class Public Class c2(Of u) Public testObject As New c1(Of u) End Class  
```  
  
 Quando a classe `c2` cria um objeto de `c1`, digite o parâmetro `u` não satisfaz a `New` restrição no parâmetro de tipo `t`.  
  
 **ID do erro:** BC32084  
  
### Para corrigir este erro  
  
-   Se o parâmetro de tipo a ser passado para o tipo genérico pode satisfazer a `Structure` ou `New` restrição, em seguida, adicione a restrição apropriada a sua definição.  
  
    ```  
    Public Class c2(Of u As Structure)  
    ```  
  
-   Se o parâmetro de tipo não puder atender o `Structure` ou `New` restrição, em seguida, passe para o tipo genérico. Você deve passar algo como o argumento de tipo.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Classe \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Tipos de valor e referência](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)