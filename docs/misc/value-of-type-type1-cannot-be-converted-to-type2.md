---
title: "O valor do tipo &#39;&lt; type1 &gt;&#39; n&#227;o pode ser convertido em &#39;&lt; type2 &gt;&#39; | Microsoft Docs"
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
  - "bc30311"
  - "vbc30311"
helpviewer_keywords: 
  - "BC30311"
ms.assetid: e3a513d4-2a1e-46d6-b592-b2e756b89d7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O valor do tipo &#39;&lt; type1 &gt;&#39; n&#227;o pode ser convertido em &#39;&lt; type2 &gt;&#39;
Uma instrução tenta converter um tipo de dados para outro de forma que não está definida. Possíveis causas desse erro incluem o seguinte:  
  
-   Uma conversão especifica dois tipos de dados entre os quais não exista nenhuma conversão. Um exemplo disso é uma conversão de um `Boolean` de valor para o `Date` tipo.  
  
-   Uma inicialização de uma matriz não inclui chaves \(`{}`\) seguir um `New` cláusula. Nesse caso, \< type2 \> tem o formato ' 1\-matriz dimensional de \< tipo \>'.  
  
 **ID do erro:** BC30311  
  
### Para corrigir este erro  
  
-   Verifique se que a expressão pode ser convertida para o tipo de dados de destino.  
  
-   Se \< type2 \> é uma matriz, certifique\-se de `New` cláusula contém parênteses e chaves após o nome do tipo. O código a seguir ilustra a inicialização correta de uma matriz.  
  
    ```  
    Dim anIntArray As Integer() = New Integer() {}  
    ```  
  
## Consulte também  
 [Conversões de tipo no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Como inicializar uma variável de matriz no Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)