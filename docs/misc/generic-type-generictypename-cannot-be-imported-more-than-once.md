---
title: "O tipo gen&#233;rico &#39;&lt; generictypename &gt;&#39; n&#227;o pode ser importado mais de uma vez | Microsoft Docs"
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
  - "BC32086"
  - "vbc32086"
helpviewer_keywords: 
  - "BC32086"
ms.assetid: d93bae4b-3224-4a6e-a072-8ce231084519
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo gen&#233;rico &#39;&lt; generictypename &gt;&#39; n&#227;o pode ser importado mais de uma vez
Um [Instrução Imports \(tipo e namespace .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) Especifica um tipo genérico que já foram importado com parametrização de tipo diferente.  
  
 Você pode declarar vários tipos construídos a partir de um tipo genérico, porque você não redefinir o tipo genérico, declarando um tipo construído. No entanto, se você importar mais de uma vez um tipo genérico, que é o equivalente de várias definições.  
  
 **ID do erro:** BC32086  
  
### Para corrigir este erro  
  
1.  Se o arquivo de origem que contém esse `Imports` instrução também contém outro `Imports` instrução, especificando o mesmo tipo genérico, remova uma delas.  
  
2.  Se você precisa importar o mesmo tipo genérico com parametrizações automáticas de tipo diferente, use vários arquivos de origem.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)