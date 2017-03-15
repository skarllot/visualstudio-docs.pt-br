---
title: "O tipo &#39;&lt; typename &gt;&#39; deve definir o operador &#39;&lt; determinantoperator &gt;&#39; para ser usado em uma express&#227;o &#39;&lt; shortcircuitoperator &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33035"
  - "vbc33035"
helpviewer_keywords: 
  - "BC33035"
ms.assetid: 50a0a39f-63cd-4100-aea9-91b5b6ab5bbf
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; deve definir o operador &#39;&lt; determinantoperator &gt;&#39; para ser usado em uma express&#227;o &#39;&lt; shortcircuitoperator &gt;&#39;
Um [Operador AndAlso](/dotnet/visual-basic/language-reference/operators/andalso-operator) ou um [Operador OrElse](/dotnet/visual-basic/language-reference/operators/orelse-operator) usa operandos de um tipo de classe ou estrutura, quando essa classe ou estrutura não define um operador necessário.  
  
 Porque você não pode definir um operador Short\-circuiting \(`AndAlso` ou `OrElse`\) diretamente, você deve definir os operadores lógicos e determinantes correspondentes. A tabela a seguir mostra os operadores necessários.  
  
|Operador Short\-circuiting|Operador lógico|Operador determinante|  
|--------------------------------|---------------------|---------------------------|  
|`AndAlso`|[Operador And](/dotnet/visual-basic/language-reference/operators/and-operator)|[Operador IsFalse](/dotnet/visual-basic/language-reference/operators/isfalse-operator)|  
|`OrElse`|[Operador Or](/dotnet/visual-basic/language-reference/operators/or-operator)|[Operador IsTrue](/dotnet/visual-basic/language-reference/operators/istrue-operator)|  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] usa esses operadores lógicos e determinantes para construir a lógica de curto\-circuito para `AndAlso` ou `OrElse`. Para que isso funcione corretamente, os operandos e o valor de retorno de seu `And` ou `Or` definição deve ser do tipo recipiente, ou seja, o tipo de classe ou estrutura na qual você está definindo `And` ou `Or`.  
  
 **ID do erro:** BC33035  
  
### Para corrigir este erro  
  
-   Definir o `And` e `IsFalse` operadores, ou o `Or` e `IsTrue` na classe ou estrutura usada para o tipo de operando dos operadores a `AndAlso` ou `OrElse` operador. Certifique\-se de que os operandos de `And` ou `Or` são do tipo da classe ou estrutura na qual você definiu.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operadores lógicos e bit a bit no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators)