---
title: "Declara&#231;&#227;o de namespace com prefixo n&#227;o pode ter um valor vazio em literais XML | Microsoft Docs"
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
  - "bc31184"
  - "vbc31184"
helpviewer_keywords: 
  - "BC31184"
ms.assetid: dde656b4-df3b-4a2e-8871-4e14832ca778
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#227;o de namespace com prefixo n&#227;o pode ter um valor vazio em literais XML
Uma declaração de namespace XML em um literal XML não inclui um valor de namespace. Por exemplo, o código a seguir fará com que esse erro:  
  
```vb#  
Dim book = <book xmlns:ns=""/>  
```  
  
 **ID do erro:** BC31184  
  
### Para corrigir este erro  
  
-   Incluir um namespace válido na declaração de namespace XML, ou remova a declaração de namespace XML literal XML.  
  
     Como alternativa, você pode usar o `Imports` instrução para identificar um prefixo de namespace para o namespace vazio. Por exemplo:  
  
    ```vb#  
    Imports <xmlns:ns="">  
    ```  
  
## Consulte também  
 [Literais XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Instrução Imports \(namespace XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)