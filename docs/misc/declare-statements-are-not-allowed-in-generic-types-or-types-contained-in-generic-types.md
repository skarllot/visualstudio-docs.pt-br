---
title: "Instru&#231;&#245;es &#39;Declare&#39; n&#227;o s&#227;o permitidas em tipos gen&#233;ricos ou tipos contidos em tipos gen&#233;ricos | Microsoft Docs"
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
  - "BC32075"
  - "vbc32075"
helpviewer_keywords: 
  - "BC32075"
ms.assetid: c620b67e-70f8-42ac-8292-e9ea484904c3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es &#39;Declare&#39; n&#227;o s&#227;o permitidas em tipos gen&#233;ricos ou tipos contidos em tipos gen&#233;ricos
Um `Declare` instrução aparece como parte de uma classe genérica ou estrutura, ou uma classe ou estrutura declarada dentro de uma classe genérica ou estrutura.  
  
 Visual Basic e o .NET Framework atualmente não suportam qualquer combinação de referências externas e tipos genéricos. O compilador precisa de todos os parâmetros e o tipo de retorno de um procedimento externo para chamá\-lo corretamente.  
  
 **ID do erro:** BC32075  
  
### Para corrigir este erro  
  
-   Mova o `Declare` instrução fora do escopo de qualquer genérico digite ou removê\-lo completamente.  
  
## Consulte também  
 [Instrução Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)