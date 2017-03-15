---
title: "Instru&#231;&#227;o &#39;Return&#39; em Sub ou Set n&#227;o pode retornar um valor | Microsoft Docs"
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
  - "bc30647"
  - "vbc30647"
helpviewer_keywords: 
  - "BC30647"
ms.assetid: d4c05c28-d650-4f49-976e-650d84802036
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o &#39;Return&#39; em Sub ou Set n&#227;o pode retornar um valor
`Sub` procedimentos e propriedade `Set` procedimentos não podem retornar valores.  
  
 **ID do erro:** BC30647  
  
### Para corrigir este erro  
  
-   Alterar o procedimento atual para uma função ou um `Get` procedimento de propriedade se o procedimento atual faz parte de uma propriedade.  
  
-   Efetivamente, você pode retornar valores de `Sub` procedimentos modificando o valor dos parâmetros passados por referência usando o `ByRef` palavra\-chave.  
  
## Consulte também  
 [Instrução Return](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Subprocedimentos](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimentos de função](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)