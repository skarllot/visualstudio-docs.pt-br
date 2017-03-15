---
title: "Option Strict Custom s&#243; pode ser usado como uma op&#231;&#227;o para o compilador de linha de comando (vbc.exe) | Microsoft Docs"
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
  - "vbc31141"
  - "bc31141"
helpviewer_keywords: 
  - "BC31141"
ms.assetid: c32ae8ff-aacc-40b4-960a-6f2d5d246671
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict Custom s&#243; pode ser usado como uma op&#231;&#227;o para o compilador de linha de comando (vbc.exe)
O `Option Strict` instrução usa apenas `On` e `Off` como argumentos; `Option Strict Custom` não é permitido.  
  
 Use o `/optionstrict:custom` opção de compilador para avisar quando a semântica de linguagem estrita não é respeitada.  
  
 **ID do erro:** BC31141  
  
### Para corrigir este erro  
  
1.  Remover `Option Strict Custom` do código\-fonte.  
  
2.  Especifique o `/optionstrict:custom` opção. Para obter mais informações, consulte [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
## Consulte também  
 [Instrução Option \<keyword\>](../Topic/Option%20%3Ckeyword%3E%20Statement.md)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)