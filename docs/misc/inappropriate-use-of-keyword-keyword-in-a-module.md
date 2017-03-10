---
title: "Uso inadequado da palavra-chave &lt; palavra-chave &gt; em um m&#243;dulo | Microsoft Docs"
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
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Uso inadequado da palavra-chave &lt; palavra-chave &gt; em um m&#243;dulo
Módulos não têm instâncias, suporte a herança ou implementar interfaces. Portanto, as seguintes palavras\-chave não se aplicam a uma declaração de módulo:  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Particular](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protegido](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Estático](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 As palavras\-chave só tem suportadas em um [Instrução Module](/dotnet/visual-basic/language-reference/statements/module-statement) são [Público](/dotnet/visual-basic/language-reference/modifiers/public) e [Friend](/dotnet/visual-basic/language-reference/modifiers/friend).  
  
 Além disso, você não pode usar o [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) instrução ou o [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement) no bloco de declaração do módulo.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42028  
  
### Para corrigir este erro  
  
-   Se você pretender este elemento de programação para que seja um módulo, use apenas o `Public` ou `Friend` palavra\-chave na sua declaração. Por padrão, um módulo usa `Friend` se você não especificar seu nível de acesso.  
  
-   Se você pretende criar instâncias deste elemento de programação, declare\-o como uma classe. Você pode usar as palavras\-chave que se aplicam a uma declaração de classe.  
  
## Consulte também  
 [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement)