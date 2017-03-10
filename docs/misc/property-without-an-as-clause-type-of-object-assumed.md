---
title: "Propriedade sem uma cl&#225;usula &#39;As&#39;; tipo de objeto assumido | Microsoft Docs"
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
  - "BC42022"
  - "vbc42022"
helpviewer_keywords: 
  - "BC42022"
ms.assetid: 3379692b-8278-4488-878a-0afb76e554b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade sem uma cl&#225;usula &#39;As&#39;; tipo de objeto assumido
Uma declaração de propriedade não especifica um `As` cláusula.  
  
 Um `As` cláusula identifica um tipo de dados a ser associado um elemento de programação. Em um [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement), ela especifica o tipo de dados do valor que a propriedade `Get` procedimento retorna para o código de chamada. Se você não incluir um `As` cláusula de `Property` instrução, tipo de dados a propriedade do padrão é `Object`.  
  
 Por padrão, essa mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC42022  
  
### Para corrigir este erro  
  
-   Incluir um `As` cláusula o `Property` para especificar o tipo de dados da propriedade.  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement)