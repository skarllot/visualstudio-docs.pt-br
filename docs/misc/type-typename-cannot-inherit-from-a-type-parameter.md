---
title: "O tipo &#39;&lt; typename &gt;&#39; n&#227;o pode herdar de um par&#226;metro de tipo | Microsoft Docs"
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
  - "bc32055"
  - "vbc32055"
helpviewer_keywords: 
  - "BC32055"
ms.assetid: 97af7cad-6e40-41e3-892d-1fbcbd86356d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; n&#227;o pode herdar de um par&#226;metro de tipo
Uma classe ou interface inclui um [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement) especificando um parâmetro de tipo genérico.  
  
 Um tipo não pode herdar de um tipo que ainda não foi definido. Herança envolve a capacidade de reutilizar os membros da classe base, que por sua vez requer que esses membros estejam definidos. Um parâmetro de tipo genérico é um espaço reservado que deve ser substituído por um tipo específico fornecido por um argumento de tipo. Portanto, um tipo não pode herdar de espaço reservado.  
  
 **ID do erro:** BC32055  
  
### Para corrigir este erro  
  
-   Se o tipo que herda deve herdar de outro tipo, use um tipo específico em vez de um parâmetro de tipo.  
  
-   Se o tipo base deve ser representado por um parâmetro de tipo genérico, nenhum outro tipo pode herdar dele. Remover o [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement).  
  
## Consulte também  
 [NÃO está em compilação: Herança no Visual Basic](http://msdn.microsoft.com/pt-br/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)