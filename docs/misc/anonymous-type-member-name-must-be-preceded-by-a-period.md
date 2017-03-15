---
title: "Nome do membro de tipo an&#244;nimo deve ser precedido por um per&#237;odo | Microsoft Docs"
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
  - "vbc36575"
  - "bc36575"
helpviewer_keywords: 
  - "BC36575"
ms.assetid: b87be29e-39f0-4830-9969-608d71137e3e
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nome do membro de tipo an&#244;nimo deve ser precedido por um per&#237;odo
Na lista de inicializadores de objeto para uma declaração de tipo anônimo, um novo nome de membro ao qual é atribuído um valor deve ser precedido por um ponto. O exemplo a seguir mostra um válida e uma declaração inválida:  
  
```vb#  
' Valid.  
Dim instanceName1 = New With {.memberName = 10}  
' Invalid declaration that causes this error.  
' Dim instanceName2 = New With {memberName = 10}  
```  
  
 **ID do erro:** BC36575  
  
### Para corrigir este erro  
  
-   Adicione um ponto antes do nome do membro.  
  
## Consulte também  
 [Tipos anônimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)