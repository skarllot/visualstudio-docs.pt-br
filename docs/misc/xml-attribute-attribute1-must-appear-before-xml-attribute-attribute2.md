---
title: "Atributo XML &#39;attribute1&#39; deve aparecer antes do atributo XML &#39;attribute2&#39; | Microsoft Docs"
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
  - "bc31157"
  - "vbc31157"
helpviewer_keywords: 
  - "BC31157"
ms.assetid: d8d8769e-533d-454e-b145-99955ce45cc5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Atributo XML &#39;attribute1&#39; deve aparecer antes do atributo XML &#39;attribute2&#39;
Atributos em um literal de documento XML são especificados em uma ordem inválida. Ordem de atributo válido para um literal de documento XML é baseada na especificação XML 1.0. Por exemplo, o `encoding` atributo de um literal de documento XML deve seguir imediatamente o `version` atributo.  
  
 **ID do erro:** BC31157  
  
### Para corrigir este erro  
  
-   Atualize a ordem de atributo para o literal de documento XML usando as instruções especificadas na especificação XML 1.0.  
  
## Consulte também  
 [Especificação dos literais XML e do XML 1.0](/dotnet/visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification)   
 [Literal de documento XML](/dotnet/visual-basic/language-reference/xml-literals/xml-document-literal)   
 [Literais XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)