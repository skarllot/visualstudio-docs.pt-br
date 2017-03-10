---
title: "Argumentos de tipo inferidos para o m&#233;todo &#39;&lt; procedurename &gt;&#39; resultam nos seguintes avisos: &lt; warninglist &gt; | Microsoft Docs"
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
  - "bc41006"
  - "vbc41006"
helpviewer_keywords: 
  - "BC41006"
ms.assetid: c789ffa9-0273-47f6-8915-78fc6a7d3d6d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos de tipo inferidos para o m&#233;todo &#39;&lt; procedurename &gt;&#39; resultam nos seguintes avisos: &lt; warninglist &gt;
Um procedimento genérico é chamado sem fornecer quaisquer argumentos de tipo e o resultado de argumentos de tipo inferido em um ou mais avisos.  
  
 Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o tipo genérico. Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo. Se os tipos inferidos causam ambiguidade, ou se eles criam uma situação que pode levar a resultados inesperados, o compilador gera esse aviso.  
  
 Um *restrição* em um tipo de parâmetro limita quais argumentos de tipo podem ser passados para ele. Por exemplo, um parâmetro de tipo pode ser restringido a ser uma classe que implementa o <xref:System.IComparable%601> interface. Para obter mais informações, consulte "Restrições" em [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC41006  
  
### Para corrigir este erro  
  
-   Fornece argumentos de tipo para o procedimento genérico para que o compilador não precise inferi\-los.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)