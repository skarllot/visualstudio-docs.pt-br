---
title: "M&#233;todos de extens&#227;o devem declarar pelo menos um par&#226;metro | Microsoft Docs"
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
  - "vbc36552"
  - "bc36552"
helpviewer_keywords: 
  - "BC36552"
ms.assetid: a8cc8cdd-cdb5-42ca-b5a1-c9a71abd46eb
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos de extens&#227;o devem declarar pelo menos um par&#226;metro
Métodos de extensão devem declarar pelo menos um parâmetro. O primeiro parâmetro especifica que tipo para estender.  
  
 Um método de extensão sem parâmetros não é válido porque o primeiro parâmetro especifica o tipo de dados o método estende. O primeiro parâmetro é associado à instância do tipo de dados que chama o método.  
  
 **ID do erro:** BC36552  
  
### Para corrigir este erro  
  
-   Adicione um parâmetro do tipo que seu método estende.  
  
## Exemplo  
 O primeiro parâmetro no exemplo a seguir indica que o `Print` método estende o `String` tipo de dados.  
  
```  
<Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Quando o método de extensão é chamado como segue, parâmetro `str` no método é associado a `greeting`, a instância de `String` que chama `Print`. O compilador usará `greeting` como o argumento para o método de extensão `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Parâmetros e argumentos de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments)   
 [Procedimentos](/dotnet/visual-basic/programming-guide/language-features/procedures/index)