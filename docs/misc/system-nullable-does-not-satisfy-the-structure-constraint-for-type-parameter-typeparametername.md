---
title: "&#39;System. Nullable&#39; n&#227;o satisfaz a restri&#231;&#227;o &#39;Structure&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; | Microsoft Docs"
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
  - "bc32115"
  - "vbc32115"
helpviewer_keywords: 
  - "BC32115"
ms.assetid: 98053645-fa76-4826-a7c1-f1bdf3511863
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System. Nullable&#39; n&#227;o satisfaz a restri&#231;&#227;o &#39;Structure&#39; para o par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39;
Um tipo genérico é invocado passando um argumento de tipo de <xref:System.Nullable%601> para um parâmetro de tipo com uma `Structure` restrição.  
  
 O common language runtime \(CLR\) proíbe especificamente a <xref:System.Nullable%601> estrutura como um argumento de tipo a mesmo. Embora ele seja uma estrutura e caso contrário, satisfaria uma `Structure` restrição, usá\-lo recursivamente pode levar a construções inadequadas, como `Nullable(Of Nullable(Of Nullable))`.  
  
 **ID do erro:** BC32115  
  
### Para corrigir este erro  
  
-   Remova o `Structure` restrição do parâmetro de tipo ou altere o argumento de tipo para algum valor de tipo diferente de <xref:System.Nullable%601>.  
  
## Consulte também  
 <xref:System.Nullable%601>   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)