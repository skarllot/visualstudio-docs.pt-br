---
title: "Declara&#231;&#227;o de vari&#225;vel sem uma cl&#225;usula &#39;As&#39;; tipo de objeto assumido | Microsoft Docs"
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
  - "BC42020"
  - "vbc42020"
helpviewer_keywords: 
  - "BC42020"
ms.assetid: 9422b16d-39b5-4d49-b697-608226ccafea
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#227;o de vari&#225;vel sem uma cl&#225;usula &#39;As&#39;; tipo de objeto assumido
Uma declaração de variável não especifica um `As` cláusula.  
  
 Um `As` cláusula identifica um tipo de dados a ser associado um elemento de programação. Em um [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement), ela especifica o tipo de dados da variável ou variáveis. Se você não incluir um `As` cláusula de `Dim` instrução, o tipo de dados padrão é `Object`.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42020  
  
### Para corrigir este erro  
  
-   Incluir um `As` cláusula o `Dim` para especificar o tipo de dados.  
  
## Consulte também  
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Declaração de variável](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)