---
title: "Tipos de dados do tipo de par&#226;metros no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; typename &gt;&#39; n&#227;o podem ser inferidos destes argumentos porque h&#225; mais de um tipo poss&#237;vel | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36655"
  - "vbc36652"
  - "vbc36655"
  - "bc36652"
helpviewer_keywords: 
  - "BC36655"
  - "BC36652"
ms.assetid: 49836f20-c877-4267-8bdc-6f6d108fb8c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados do tipo de par&#226;metros no m&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; definido em &#39;&lt; typename &gt;&#39; n&#227;o podem ser inferidos destes argumentos porque h&#225; mais de um tipo poss&#237;vel
Tipos de dados do tipo de parâmetros no método de extensão '\< methodname \>' definido em '\< typename \>' não podem ser inferidos destes argumentos porque há mais de um tipo possível. Especificar os dados de tipos explicitamente podem corrigir esse erro.  
  
 Foi feita uma tentativa para usar inferência de tipo para determinar o tipo \(ou tipos\) do parâmetro de tipo \(ou parâmetros\) em uma chamada para um método de extensão genérica. O compilador encontrar mais de um tipo de dados para um ou mais dos parâmetros de tipo e relata esse erro.  
  
> [!NOTE]
>  Quando especificar argumentos não é uma opção \(por exemplo, para operadores de consulta em expressões de consulta\), a mensagem de erro aparece sem a segunda frase.  
  
 O código a seguir demonstra o erro.  
  
```vb#  
Option Strict Off Imports System.Runtime.CompilerServices Module Module1 Sub Main() Dim caller As New Class1 '' Not valid. 'caller.targetExtension(1, "2") End Sub <Extension()> _ Sub targetExtension(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **ID do erro:** BC36655 \(dentro de [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)] consultas\) e BC36652 \(fora de consultas\)  
  
### Para corrigir este erro  
  
-   Se o erro é exibido fora de uma consulta, tente especificar o tipo de dados do parâmetro de tipo ou parâmetros explicitamente:  
  
    ```  
    caller.targetExtension(Of Integer)(1, "2") caller.targetExtension(Of String)(1, "2")  
    ```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)