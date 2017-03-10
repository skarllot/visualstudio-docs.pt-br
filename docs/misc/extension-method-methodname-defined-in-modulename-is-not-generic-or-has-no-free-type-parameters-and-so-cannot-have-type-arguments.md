---
title: "M&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; modulename &gt;&#39; n&#227;o &#233; gen&#233;rico (ou n&#227;o tem nenhum par&#226;metro de tipo livre) e portanto n&#227;o pode ter argumentos de tipo | Microsoft Docs"
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
  - "bc36907"
  - "vbc36907"
helpviewer_keywords: 
  - "BC36907"
ms.assetid: 45191e93-89d1-48ec-99a5-ff9661a2a6ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; modulename &gt;&#39; n&#227;o &#233; gen&#233;rico (ou n&#227;o tem nenhum par&#226;metro de tipo livre) e portanto n&#227;o pode ter argumentos de tipo
Foi especificado um argumento de tipo em uma chamada para um método de extensão que não tem nenhum parâmetro genérico ou não tem nenhum parâmetro genérico para o qual um tipo não tiver sido especificado. Por exemplo, o código a seguir causa esse erro.  
  
```vb#  
' The extension method is not generic. <Extension()> _ Sub Example(ByVal str As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
Dim str = "hi" '' The call to Example specifies a type argument. '' Not valid. 'str.Example(Of String)()  
```  
  
 **ID do erro:** BC36907  
  
### Para corrigir este erro  
  
-   Adicione um parâmetro de tipo para a definição do método de extensão.  
  
-   Remova o argumento type extra da chamada de procedimento.  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)