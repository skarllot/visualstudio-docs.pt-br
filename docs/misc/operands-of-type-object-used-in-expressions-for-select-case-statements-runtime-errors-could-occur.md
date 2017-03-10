---
title: "Operandos do tipo objeto usados em express&#245;es para instru&#231;&#245;es de &#39;Select&#39;, &#39;Case&#39;; poder&#227;o ocorrer erros de tempo de execu&#231;&#227;o | Microsoft Docs"
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
  - "vbc42036"
  - "bc42036"
helpviewer_keywords: 
  - "BC42036"
ms.assetid: f11e9c9f-aa66-4eb1-8f49-abf713bef885
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operandos do tipo objeto usados em express&#245;es para instru&#231;&#245;es de &#39;Select&#39;, &#39;Case&#39;; poder&#227;o ocorrer erros de tempo de execu&#231;&#227;o
A `Select`...`Case` construção usa uma ou mais expressões do [Tipo de dados Object](/dotnet/visual-basic/language-reference/data-types/object-data-type).  
  
 Quando uma variável ou expressão for avaliada como `Object`, o compilador deve executar *ligação tardia*, que causa operações extras em tempo de execução. Ele também expõe sua aplicação a potenciais erros em tempo de execução. Por exemplo, se você atribuir um <xref:System.Windows.Forms.Form> para um `Object` variável e, em seguida, tentar compará\-lo com um número, o tempo de execução lança um <xref:System.InvalidCastException> porque o Visual Basic não pode converter uma <xref:System.Windows.Forms.Form> objeto como um valor numérico.  
  
 As expressões em uma `Select`...`Case` construção todos deve ser do mesmo tipo de dados ou de dados relacionados tipos que podem ser convertidos em si. Isso ocorre porque cada `Case` instrução compara a pelo menos um valor em relação à expressão de teste no qual o `Select`...`Case` com base em construção.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42036  
  
### Para corrigir este erro  
  
-   Se possível, organize todas as expressões para avaliar a tipos de dados para o qual os operadores de comparação são definidos.  
  
## Consulte também  
 [Instrução Select...Case](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Operadores aritméticos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Operadores de comparação no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)