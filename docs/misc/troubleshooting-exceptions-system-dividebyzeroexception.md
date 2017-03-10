---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.DivideByZeroException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe DivideByZeroException"
ms.assetid: ddc79201-3ba1-455f-8496-edaad792ccf1
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.DivideByZeroException
Um <xref:System.DivideByZeroException> exceção é lançada quando há uma tentativa de dividir um valor inteiro ou decimal por zero.  
  
## Dicas associadas  
 **Verifique se que o valor do denominador não é zero antes de executar uma operação de divisão.**  
 Dividir um valor de ponto flutuante por zero resulta em infinito positivo, infinito negativo ou não um número \(NaN\), de acordo com as regras de aritmética IEEE. Operações de ponto flutuante nunca lançam uma exceção.  
  
## Consulte também  
 <xref:System.DivideByZeroException>   
 [Operadores aritméticos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)