---
title: "&#39;&lt; parametername &gt;&#39; j&#225; est&#225; declarado como um par&#226;metro de tipo deste m&#233;todo | Microsoft Docs"
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
  - "bc32089"
  - "vbc32089"
helpviewer_keywords: 
  - "BC32089"
ms.assetid: 5e440b4b-f62b-4ff5-9148-2372d4752bf6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; parametername &gt;&#39; j&#225; est&#225; declarado como um par&#226;metro de tipo deste m&#233;todo
Um procedimento genérico define um parâmetro normal ou uma variável local com o mesmo nome como um parâmetro de tipo.  
  
 Cada parâmetro de um procedimento, incluindo cada parâmetro de tipo de um procedimento genérico, deve ter um nome distinto de todos os outros parâmetros. Como parâmetros de procedimento são usados como variáveis locais, qualquer variável local declarada dentro do procedimento também deve ter um nome distinto de todos os parâmetros e parâmetros de tipo.  
  
 **ID do erro:** BC32089  
  
### Para corrigir este erro  
  
-   Altere o nome do parâmetro normal ou variável local.  
  
## Consulte também  
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de parâmetros](/dotnet/visual-basic/language-reference/statements/parameter-list)