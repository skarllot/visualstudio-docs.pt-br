---
title: "O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; tem o mesmo nome que um par&#226;metro de tipo de um tipo de delimitador | Microsoft Docs"
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
  - "vbc40048"
  - "bc40048"
helpviewer_keywords: 
  - "BC40048"
ms.assetid: d5428b36-88d3-42c4-a096-cbc7bb9571f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; tem o mesmo nome que um par&#226;metro de tipo de um tipo de delimitador
Um parâmetro de tipo de um tipo genérico é declarado com o mesmo nome que um parâmetro de tipo de um tipo genérico.  
  
 Na lista de parâmetros de tipo de um tipo genérico, cada parâmetro de tipo deve ter um nome distinto de todos os nomes a seguir:  
  
-   Cada outro parâmetro do tipo na mesma lista de parâmetros de tipo,  
  
-   Cada parâmetro de tipo na lista de parâmetros de tipo de qualquer tipo genérico, e  
  
-   O nome do tipo genérico em si.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40048  
  
### Para corrigir este erro  
  
-   Renomeie o parâmetro do tipo para ser distinto de cada nome citado na lista nesta página de Ajuda.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)