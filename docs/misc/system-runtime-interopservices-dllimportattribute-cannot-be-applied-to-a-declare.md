---
title: "&#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a &#39;Declare&#39; | Microsoft Docs"
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
  - "bc31523"
  - "vbc31523"
helpviewer_keywords: 
  - "BC31523"
ms.assetid: 04c8a14f-9286-4f9a-aad5-a0555e5f09f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a &#39;Declare&#39;
O `DllImportAttribute` atributo foi aplicado a um `Declare` função. Esse atributo só pode ser usado com um vazio `Function` ou `Sub`.  
  
 **ID do erro:** BC31523  
  
### Para corrigir este erro  
  
1.  Remover o `DllImportAttribute` do atributo do `Declare` instrução.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Instrução Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)