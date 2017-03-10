---
title: "N&#227;o &#233; poss&#237;vel inferir um tipo anul&#225;vel para a vari&#225;vel &#39;&lt; variablename &gt;&#39; | Microsoft Docs"
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
  - "bc36628"
  - "vbc36628"
helpviewer_keywords: 
  - "BC36628"
ms.assetid: 3e92ae19-6a19-4b0b-9dd9-fba31cdb85a6
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel inferir um tipo anul&#225;vel para a vari&#225;vel &#39;&lt; variablename &gt;&#39;
Não é possível inferir um tipo anulável de um tipo de referência, como uma matriz, uma classe ou um `String`. O valor do qual o tipo de dados é inferido deve ser um tipo de valor. O código a seguir ilustra esse erro.  
  
```vb#  
'' Not valid.   
'Dim arrList? = New ArrayList  
'Dim except? = New Exception  
'Dim obj? = New Object  
'Dim stringVar? = "Open the application."  
  
' Valid.  
Dim intVar? = 10  
```  
  
 **ID do erro:** BC36628  
  
### Para corrigir este erro  
  
-   Remova a designação permite valor nula.  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)