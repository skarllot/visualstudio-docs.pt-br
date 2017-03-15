---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.OverflowException | Microsoft Docs"
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
  - "Classe OverflowException"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.OverflowException
Um <xref:System.OverflowException> exceção é lançada quando uma operação aritmética ou de conversão em um contexto selecionado resulta em um estouro. Um estouro ocorre quando uma operação produz um valor muito grande para o tipo de destino, infinito ou não é um número \(NaN\).  
  
## Dicas associadas  
 **Ao converter de um número, o valor deve ser um número válido menor que infinito.**  
 Um valor de origem não pode ser infinito ou não um número.  
  
 **Certifique\-se de que não está dividindo por zero.**  
 Divisão por zero normalmente gerará essa exceção.  
  
## Comentários  
 Em linguagens que detectam estouro, <xref:System.OverflowException> é a exceção que é lançada quando ocorre estouro. Por exemplo, no c\#, o `checked` palavra\-chave é usada para detectar condições de estouro. Um <xref:System.OverflowException> exceção ocorre apenas em um contexto marcada.  
  
 Para obter um resultado de uma operação aritmética integral ou tipo decimal ou conversão que está fora do intervalo do tipo de destino:  
  
-   Em um contexto marcada, ocorrerá um erro de tempo de compilação se a operação for uma expressão constante. Caso contrário, um <xref:System.OverflowException> exceção será gerada se a operação é executada em tempo de execução.  
  
-   Em um contexto desmarcado, o resultado será truncado ao descartar quaisquer bits de ordem superior que não cabem no tipo de destino.  
  
 Para obter informações sobre os intervalos de valores de tipos de dados, consulte [Tipos de dados](/dotnet/visual-basic/language-reference/data-types/data-type-summary), [Tabela de tipos integrais](/dotnet/csharp/language-reference/keywords/integral-types-table), ou [Tabela de tipos de ponto flutuante](/dotnet/csharp/language-reference/keywords/floating-point-types-table).  
  
## Consulte também  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)