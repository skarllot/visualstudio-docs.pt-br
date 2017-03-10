---
title: "Op&#231;&#227;o /win32manifest ignorada | Microsoft Docs"
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
  - "vbc2034"
  - "bc2034"
helpviewer_keywords: 
  - "BC2034"
ms.assetid: 8009553a-f6ba-4d2b-8ddd-8a9357bc928e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Op&#231;&#227;o /win32manifest ignorada
Opção \/win32manifest ignorada. Ele pode ser especificado somente quando o destino é um assembly.  
  
 O compilador do Visual Basic foi passado a `/win32manifest` opção de compilador quando o `/target` opção é definida como `module`.  
  
 **ID do erro:** BC2034  
  
### Para corrigir este erro  
  
1.  Remover o `/win32manifest` opção de compilador ou conjunto de `/target` opção `exe`, `winexe`, ou `library`.  
  
## Consulte também  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/win32manifest](/dotnet/visual-basic/reference/command-line-compiler/win32manifest)   
 [Compilador de linha de comando do Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)