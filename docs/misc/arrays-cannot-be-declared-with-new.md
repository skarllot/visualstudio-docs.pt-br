---
title: "Matrizes n&#227;o podem ser declaradas com &#39;New&#39; | Microsoft Docs"
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
  - "vbc30053"
  - "bc30053"
helpviewer_keywords: 
  - "BC30053"
ms.assetid: aa55f3b7-2045-497b-9543-5ec6e2b74fe2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Matrizes n&#227;o podem ser declaradas com &#39;New&#39;
O `New` palavra\-chave pode aparecer somente na parte de inicialização de uma declaração de matriz. Isso significa `New` deve estar no lado direito do sinal de igual \(`=`\) para que ele possa criar um novo tipo de matriz a ser atribuído à variável de matriz.  
  
 O atalho para classe de inicialização não está disponível para matrizes. As seguintes duas linhas de código são válidas e são equivalentes porque elas inicializam um objeto de uma classe.  
  
```  
Dim formA as Form = New Form Dim formA as New Form  
```  
  
 No entanto, a inicialização de matriz não pode usar o mesmo atalho da classe de inicialização.  
  
 Observe que o `New` cláusula para uma matriz deve conter entre parênteses, `()`, e as chaves, `{}`. Os parênteses especificam que o novo tipo é uma matriz, e as chaves fornecem os valores de inicialização. O compilador requer as chaves mesmo se elas estiverem vazias, ou seja, mesmo se você não estiver inicializando qualquer um dos valores de matriz.  
  
 **ID do erro:** BC30053  
  
### Para corrigir este erro  
  
-   Substitua uma instrução, como `Dim myDates() As New Date` com uma instrução como `Dim myDates() As Date = New Date() {}`.  
  
## Consulte também  
 [Matrizes](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Como inicializar uma variável de matriz no Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)