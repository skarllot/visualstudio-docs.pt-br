---
title: "Vari&#225;vel de recurso &#39; using&#39; deve ter uma inicializa&#231;&#227;o expl&#237;cita. | Microsoft Docs"
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
  - "vbc36011"
  - "bc36011"
helpviewer_keywords: 
  - "BC36011"
ms.assetid: 5db996a6-0802-4b67-91f1-4aa9c3dd6b09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;vel de recurso &#39; using&#39; deve ter uma inicializa&#231;&#227;o expl&#237;cita.
Um `Using` declaração especifica pelo menos um recurso que ele não inicializa com um `New` cláusula.  
  
 Se você ainda não adquiriu o recurso antes de passar o controle para o `Using` bloco, o `Using` instrução deve adquirir o recurso. Para fazer isso, ele deve criar um objeto da classe especificada, que requer um `New` cláusula.  
  
 **ID do erro:** BC36011  
  
### Para corrigir este erro  
  
-   Se você já tiver adquirido o recurso, use uma referência variável ou expressão no `Using` instrução que avalia para o recurso adquirido.  
  
     `Dim newFont As New System.Drawing.Font`  
  
     `Using newFont`  
  
-   Se você ainda não adquiriu o recurso, adicione uma `New` cláusula para o `Using` instrução.  
  
     `Using newFont as`   `New`   `System.Drawing.Font`  
  
## Consulte também  
 [Instrução Using](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Como descartar um recurso do sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)