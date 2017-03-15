---
title: "A op&#231;&#227;o /moduleassemblyname somente pode ser especificada ao criar um destino do tipo &#39;module&#39; | Microsoft Docs"
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
  - "bc2030"
  - "vbc2030"
helpviewer_keywords: 
  - "BC2030"
ms.assetid: 2ebc577b-3464-40cc-8788-9fc9d3b4f928
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A op&#231;&#227;o /moduleassemblyname somente pode ser especificada ao criar um destino do tipo &#39;module&#39;
O compilador do Visual Basic foi passado a `/moduleassemblyname` opção de compilador quando o `/target` opção é definida como um valor diferente de `module`.  
  
 **ID do erro:** BC2030  
  
### Para corrigir este erro  
  
1.  Remover o `/moduleassemblyname` opção de compilador ou conjunto de `/target` opção `module`.  
  
## Consulte também  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/moduleassemblyname](/dotnet/visual-basic/reference/command-line-compiler/moduleassemblyname)   
 [Compilador de linha de comando do Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)