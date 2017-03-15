---
title: "Declara&#231;&#227;o de namespace deve come&#231;ar com &#39;xmlns&#39; | Microsoft Docs"
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
  - "bc31187"
  - "vbc31187"
helpviewer_keywords: 
  - "BC31187"
ms.assetid: 64c6a033-7cdc-48a0-bff0-bdd045cb13ad
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#227;o de namespace deve come&#231;ar com &#39;xmlns&#39;
Foi especificado um namespace XML sem necessários `xmlns` identificador. O `xmlns` identificador deve conter somente caracteres minúsculos.  
  
 **ID do erro:** BC31187  
  
### Para corrigir este erro  
  
-   Use o `xmlns` identificador ao declarar um namespace XML. A seguir está um exemplo:  
  
    ```vb#  
    Imports <xmlns:ns="http://SampleNamespace">  
    ```  
  
## Consulte também  
 [Instrução Imports \(namespace XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [Literais XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)