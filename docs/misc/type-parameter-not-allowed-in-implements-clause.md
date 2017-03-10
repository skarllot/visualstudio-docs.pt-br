---
title: "Par&#226;metro de tipo n&#227;o permitido na cl&#225;usula &#39;Implements&#39; | Microsoft Docs"
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
  - "vbc32056"
  - "bc32056"
helpviewer_keywords: 
  - "BC32056"
ms.assetid: a62d773b-e878-4817-8638-da49849477d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metro de tipo n&#227;o permitido na cl&#225;usula &#39;Implements&#39;
Um `Implements` cláusula em um tipo genérico especifica um parâmetro de tipo como o membro a ser implementado.  
  
 Um `Implements` cláusula deve especificar uma interface e um membro. Ele pode passar um parâmetro de tipo para a interface, mas ele não pode passá\-lo para o membro, nem usá\-lo como o nome do membro.  
  
 As instruções a seguir podem gerar esse erro.  
  
```  
Class c1(Of t) Implements i1(Of t) Public Sub doSomething() Implements t End Class  
```  
  
 **ID do erro:** BC32056  
  
### Para corrigir este erro  
  
-   Especifique o nome da interface e um membro genuíno de interface após o `Implements` palavra\-chave. Você pode passar o parâmetro de tipo para a interface, se apropriado.  
  
    ```  
    Public Sub doSomething() Implements i1(Of t).doSomething  
    ```  
  
## Consulte também  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [NÃO está em compilação: Palavra\-chave Implements e a instrução Implements](http://msdn.microsoft.com/pt-br/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)