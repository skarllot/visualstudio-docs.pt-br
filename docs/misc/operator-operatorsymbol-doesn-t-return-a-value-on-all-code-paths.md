---
title: "Operador &#39;&lt; operatorsymbol &gt;&#39; n&#227;o retorna um valor em todos os caminhos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42106"
  - "bc42106"
helpviewer_keywords: 
  - "BC42106"
ms.assetid: 175b2bc9-5233-462d-97de-9d97b003cc46
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador &#39;&lt; operatorsymbol &gt;&#39; n&#227;o retorna um valor em todos os caminhos de c&#243;digo
Operador '\< operatorsymbol \>' não retorna um valor em todos os caminhos de código. Uma exceção de referência nula pode ocorrer em tempo de execução quando o resultado é usado.  
  
 Um procedimento de operador tem pelo menos um caminho possível pelo seu código que não retorna um valor.  
  
 Você pode retornar um valor de um procedimento de operador somente, incluindo\-o em um [Instrução Return](/dotnet/visual-basic/language-reference/statements/return-statement).  
  
 Se o controle passa para o `End Operator` instrução, o procedimento de operador retorna o valor padrão da propriedade tipo de dados. Para obter mais informações, consulte "Comportamento" em [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement).  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42106  
  
### Para corrigir este erro  
  
-   Verifique sua lógica de fluxo de controle e assegure\-se de que cada caminho possível termina com uma `Return` instrução. Em particular, a última instrução antes `End Operator` deve ser um `Return` instrução.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)