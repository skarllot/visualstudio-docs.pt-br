---
title: "Argumento &#39;Period&#39; deve ser menor ou igual ao argumento &#39;Life&#39; | Microsoft Docs"
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
  - "vbrFinancial_PeriodLELife"
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumento &#39;Period&#39; deve ser menor ou igual ao argumento &#39;Life&#39;
O valor da `Period` argumento, que especifica o período para o ativo a depreciação é calculada, é maior que o valor da `Life` argumento.  
  
### Para corrigir este erro  
  
-   Verifique se o `Life` e `Period` argumentos são expressos nas mesmas unidades. Por exemplo, se `Life` é medido em meses, `Period` também deve ser.  
  
## Consulte também  
 [NÃO está em compilação: Função do BDD](http://msdn.microsoft.com/pt-br/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [NÃO está em compilação: Função SYD](http://msdn.microsoft.com/pt-br/23c25672-f5dd-49ac-9893-4faa82634181)   
 [Passando argumentos por valor e por referência](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)