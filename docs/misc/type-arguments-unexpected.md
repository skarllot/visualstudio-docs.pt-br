---
title: "Argumentos de tipo inesperado | Microsoft Docs"
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
  - "vbc32088"
  - "bc32088"
helpviewer_keywords: 
  - "BC32088"
ms.assetid: a0918e90-e7ad-4edc-81e1-584e6174bb6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos de tipo inesperado
Um `Implements` cláusula fornece argumentos de tipo para o membro de interface que está implementando.  
  
 O `Implements` cláusula só deve identificar a interface e o membro que está implementando. Isso significa que, se você está declarando um procedimento genérico, o `Of` cláusula e os argumentos de tipo devem aparecer na parte principal da declaração, como fariam se você não fosse implementar um procedimento de interface.  
  
 O código a seguir pode gerar esse erro.  
  
```  
Public Interface testInterface Sub testSub(Of t)() End Interface Public Class testClass Implements testInterface Public Sub testSub() Implements testInterface.testSub(Of t)() End Sub End Class  
```  
  
 A declaração anterior de `Implements` cláusula deve parecer com a definição de interface, exceto para a possível adição de modificadores de acesso ou procedimento. O código a seguir evita o erro.  
  
```  
Public Sub testSub(Of t)() Implements testInterface.testSub  
```  
  
 **ID do erro:** BC32088  
  
### Para corrigir este erro  
  
-   Remover a lista de argumentos de tipo de `Implements` cláusula.  
  
-   Se você estiver implementando um membro genérico de interface, então coloque a lista de argumentos de tipo na parte principal da declaração, anterior a `Implements` palavra\-chave.  
  
## Consulte também  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [NÃO está em compilação: Palavra\-chave Implements e a instrução Implements](http://msdn.microsoft.com/pt-br/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)