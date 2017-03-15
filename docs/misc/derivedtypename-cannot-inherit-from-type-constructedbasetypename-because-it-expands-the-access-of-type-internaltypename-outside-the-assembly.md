---
title: "&#39;&lt; derivedtypename &gt;&#39; n&#227;o pode herdar de &lt; tipo &gt; &#39;&lt; constructedbasetypename &gt;&#39; porque ele expande o acesso do tipo &#39;&lt; internaltypename &gt;&#39; fora do assembly | Microsoft Docs"
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
  - "BC30922"
  - "vbc30922"
helpviewer_keywords: 
  - "BC30922"
ms.assetid: 81909654-7e67-4b89-81a3-25ae57f678f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; derivedtypename &gt;&#39; n&#227;o pode herdar de &lt; tipo &gt; &#39;&lt; constructedbasetypename &gt;&#39; porque ele expande o acesso do tipo &#39;&lt; internaltypename &gt;&#39; fora do assembly
Uma classe derivada ou interface tenta expandir o nível de acesso de um tipo restrito usando\-o como um argumento de tipo a uma classe base ou interface.  
  
 O código a seguir pode gerar esse erro.  
  
```  
Public Class baseClass(Of t)  
End Class  
Public Class derivedClass  
    Inherits baseClass(Of restrictedStructure)  
End Class  
Friend Structure restrictedStructure  
    Dim firstMember As Integer  
End Structure  
```  
  
 Código fora do assembly não tem permissão para acessar `restrictedStructure`. No entanto, `derivedClass` pode ser acessado de qualquer código que pode fazer referência a ela. Portanto, `derivedClass` não é possível herdar `baseClass` se ele usa `restrictedStructure` como um argumento de tipo, porque aquilo poderia expor `restrictedStructure` ao código em qualquer assembly.  
  
 **ID do erro:** BC30922  
  
### Para corrigir este erro  
  
-   Ajuste os níveis de acesso das interfaces ou classes para que o tipo derivado não expande o nível de acesso do tipo restrito.  
  
     \- ou \-  
  
-   Se você não pode ajustar os níveis de acesso, não use o tipo restrito como um argumento de tipo quando construir a classe base ou interface.  
  
## Consulte também  
 [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Níveis de acesso no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)