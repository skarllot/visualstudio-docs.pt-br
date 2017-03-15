---
title: "Interface &#39;&lt; interfacename &gt;&#39; n&#227;o &#233; implementada por esta classe | Microsoft Docs"
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
  - "bc31035"
  - "vbc31035"
helpviewer_keywords: 
  - "BC31035"
ms.assetid: 99ddabb5-20e0-4cf6-a8d4-1ca91f3c7511
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Interface &#39;&lt; interfacename &gt;&#39; n&#227;o &#233; implementada por esta classe
Um membro dessa classe ou estrutura tenta implementar um membro de uma interface que a classe ou estrutura não implementa.  
  
 **ID do erro:** BC31035  
  
### Para corrigir este erro  
  
-   Adicione um `Implements` instrução no início da classe ou estrutura de modo que ela implemente a interface apropriada.  
  
-   Remover o `Implements` palavra\-chave do membro que causa esse erro.  
  
## Consulte também  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Instrução Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)