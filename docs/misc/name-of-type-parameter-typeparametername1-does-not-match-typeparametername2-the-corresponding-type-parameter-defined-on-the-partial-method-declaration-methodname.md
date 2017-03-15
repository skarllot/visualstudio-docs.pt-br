---
title: "Nome do par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; n&#227;o coincide com &#39;&lt; typeparametername2 &gt;&#39;, o tipo correspondente definido na declara&#231;&#227;o de m&#233;todo parcial &#39;&lt; methodname &gt;&#39; do par&#226;metro | Microsoft Docs"
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
  - "vbc31443"
  - "bc31443"
helpviewer_keywords: 
  - "BC31443"
ms.assetid: 27c81cc1-325e-4e86-9d00-34f81e928076
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nome do par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; n&#227;o coincide com &#39;&lt; typeparametername2 &gt;&#39;, o tipo correspondente definido na declara&#231;&#227;o de m&#233;todo parcial &#39;&lt; methodname &gt;&#39; do par&#226;metro
Em um método parcial que inclui um ou mais parâmetros de tipo, os nomes dos parâmetros de tipo devem ser o mesmo na declaração do método e na implementação do método.  
  
 Por exemplo, a seguinte declaração e implementação causam esse erro.  
  
```vb#  
' Definition of the partial method signature with type parameter T. Partial Private Sub OnNameChanged(Of T)() End Sub  
```  
  
```vb#  
'' Implementation of the partial method with type parameter N. 'Private Sub OnNameChanged(Of N)() '    Console.WriteLine("Name was changed to " & Me.Name) 'End Sub  
```  
  
 **ID do erro:** BC31443  
  
### Para corrigir este erro  
  
-   Examine os parâmetros de tipo para determinar onde eles não coincidem. Altere os nomes conforme necessário para fazer o mesmo.  
  
## Consulte também  
 [Métodos parciais](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)