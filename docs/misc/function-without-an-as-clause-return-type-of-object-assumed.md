---
title: "Fun&#231;&#227;o sem uma cl&#225;usula &#39;As&#39;; tipo de retorno de objeto assumido | Microsoft Docs"
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
  - "BC42021"
  - "vbc42021"
helpviewer_keywords: 
  - "BC42021"
ms.assetid: c1efadf1-fba3-437b-a311-240c4d07d894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fun&#231;&#227;o sem uma cl&#225;usula &#39;As&#39;; tipo de retorno de objeto assumido
Um `Function` procedimento não especifica um `As` cláusula.  
  
 Um `As` cláusula identifica um tipo de dados a ser associado um elemento de programação. Em um [Instrução Function](/dotnet/visual-basic/language-reference/statements/function-statement), ela especifica o tipo de dados do valor de `Function` procedimento retorna para o código de chamada. Se você não incluir um `As` cláusula de `Function` tipo de instrução, os dados de retorno padrão é `Object`.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42021  
  
### Para corrigir este erro  
  
-   Incluir um `As` cláusula de `Function` instrução para especificar o tipo de dados de retorno.  
  
## Consulte também  
 [Procedimentos de função](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)