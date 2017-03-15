---
title: "Membros de inst&#226;ncia e &#39;Me&#39; n&#227;o pode ser usado dentro de uma express&#227;o lambda em estruturas | Microsoft Docs"
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
  - "vbc36638"
  - "bc36638"
helpviewer_keywords: 
  - "BC36638"
ms.assetid: 5c24a7c7-50f6-4ffb-9ed2-07e2abc4eaf3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membros de inst&#226;ncia e &#39;Me&#39; n&#227;o pode ser usado dentro de uma express&#227;o lambda em estruturas
De dentro de uma estrutura, você definiu uma expressão lambda que se refere a um membro de instância da estrutura ou usa `Me`. O código a seguir ilustra essas duas referências inválidas.  
  
```vb#  
Structure Structure1 Public InstanceMember As Integer Public Function ExampleFun() As Integer '' The error is caused by use of InstanceMember. 'Dim fun1 = Function() InstanceMember '' The error is caused by use of Me. 'Dim fun2 = Function() Me.InstanceMember 'Return fun1() End Function End Structure  
```  
  
 **ID do erro:** BC36638  
  
### Para corrigir este erro  
  
-   Atribua o membro de instância a uma variável local e use a variável local na instrução.  
  
    ```vb#  
    Public Function ExampleFunFix() As Integer Dim temp = InstanceMember Dim fun1 = Function() temp Return fun1() End Function  
    ```  
  
## Consulte também  
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Me](http://msdn.microsoft.com/pt-br/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Instrução Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)