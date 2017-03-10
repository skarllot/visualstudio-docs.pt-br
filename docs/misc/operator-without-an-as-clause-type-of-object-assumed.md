---
title: "Operador sem uma cl&#225;usula &#39;As&#39;; tipo de objeto assumido | Microsoft Docs"
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
  - "vbc41005"
  - "bc41005"
helpviewer_keywords: 
  - "BC41005"
ms.assetid: 42be84ed-7aa6-4ac0-9dd4-663e90f13e09
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador sem uma cl&#225;usula &#39;As&#39;; tipo de objeto assumido
Um procedimento de operador não especifica um `As` cláusula.  
  
 Um `As` cláusula identifica um tipo de dados a ser associado um elemento de programação. Em um [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement), ela especifica o tipo de dados do valor que o procedimento de operador retorna para o código de chamada. Se você não incluir um `As` cláusula de `Operator` tipo de instrução, os dados de retorno padrão é `Object`.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC41005  
  
### Para corrigir este erro  
  
-   Incluir um `As` cláusula de `Operator` instrução para especificar o tipo de dados de retorno.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)