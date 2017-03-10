---
title: "&#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a &#39;Get&#39; ou &#39;Set&#39; | Microsoft Docs"
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
  - "vbc31524"
  - "bc31524"
helpviewer_keywords: 
  - "BC31524"
ms.assetid: 3603e33a-a80b-448d-83e0-e5dbc9af4dcf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a &#39;Get&#39; ou &#39;Set&#39;
O `DllImportAttribute` atributo foi aplicado a um `Get` ou `Set` procedimento de propriedade.  
  
 **ID do erro:** BC31524  
  
### Para corrigir este erro  
  
1.  Remover `DllImportAttribute` de `Get` e `Set` procedimentos de propriedade.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)