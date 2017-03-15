---
title: "M&#233;todos gen&#233;ricos n&#227;o podem ser expostos ao COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30943"
  - "bc30943"
helpviewer_keywords: 
  - "BC30943"
ms.assetid: 0e3bff62-f187-4864-8520-70f6be22e869
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos gen&#233;ricos n&#227;o podem ser expostos ao COM
Um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que contém um ou mais procedimentos genéricos do componente é exportado para um componente COM.  
  
 O modelo de objeto de componente \(COM\) não oferece suporte para tipos genéricos e ele não pode interoperar com eles.  
  
 **ID do erro:** BC30943  
  
### Para corrigir este erro  
  
-   Remova o procedimento ou procedimentos genéricos do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] componente, ou não usá\-lo para interoperabilidade COM.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Interoperabilidade COM](/dotnet/visual-basic/programming-guide/com-interop/index)