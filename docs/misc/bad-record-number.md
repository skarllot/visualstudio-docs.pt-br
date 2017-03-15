---
title: "N&#250;mero de registro incorreto | Microsoft Docs"
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
  - "vbrID63"
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#250;mero de registro incorreto
O número do registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.  
  
### Para corrigir este erro  
  
1.  Verifique os cálculos usados na geração de número de registro. Verifique se as variáveis contendo o número de registro ou usado para calcular números de registro. Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.  
  
## Consulte também  
 [Instrução Option Explicit](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)