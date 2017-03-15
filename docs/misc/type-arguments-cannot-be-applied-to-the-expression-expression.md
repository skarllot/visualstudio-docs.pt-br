---
title: "Argumentos de tipo n&#227;o podem ser aplicados &#224; express&#227;o &#39;&lt; expression &gt;&#39; | Microsoft Docs"
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
  - "bc32058"
  - "vbc32058"
helpviewer_keywords: 
  - "BC32058"
ms.assetid: c6b9b49c-6fb2-47b8-a8bb-464562d3adfd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos de tipo n&#227;o podem ser aplicados &#224; express&#227;o &#39;&lt; expression &gt;&#39;
Um alias de importação é definido com um [de](/dotnet/visual-basic/language-reference/statements/of-clause) cláusula que passa os argumentos para o alias de importação de tipo.  
  
 Argumentos de tipo são usados para tipos genéricos e apenas classes, estruturas, interfaces, procedimentos e delegados podem ser genéricos. Namespaces nem importar aliases podem ser genéricos.  
  
 **ID do erro:** BC32058  
  
### Para corrigir este erro  
  
-   Remover o `Of` cláusula e seus argumentos de tipo de alias de importação.  
  
## Consulte também  
 [Instrução Imports \(tipo e namespace .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Referências e a instrução Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)   
 [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)