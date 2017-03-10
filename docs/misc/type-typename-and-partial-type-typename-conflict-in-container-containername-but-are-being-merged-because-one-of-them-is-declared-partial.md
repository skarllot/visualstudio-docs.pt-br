---
title: "O tipo &#39;&lt; typename &gt;&#39; e tipo parcial &#39;&lt; typename &gt;&#39; est&#227;o em conflito no cont&#234;iner &#39;&lt; nomecont&#234;iner &gt;&#39;, mas est&#227;o sendo mesclados porque um deles &#233; declarado parcial | Microsoft Docs"
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
  - "bc40046"
  - "vbc40046"
helpviewer_keywords: 
  - "BC40046"
ms.assetid: c243e70b-ecd5-49ef-a260-a7bb12a4a3b1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; e tipo parcial &#39;&lt; typename &gt;&#39; est&#227;o em conflito no cont&#234;iner &#39;&lt; nomecont&#234;iner &gt;&#39;, mas est&#227;o sendo mesclados porque um deles &#233; declarado parcial
Uma classe ou estrutura é exibido em várias definições no mesmo tipo de continente, e mais de uma definição não está marcado como `Partial`.  
  
 Você deve usar o [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial) palavra\-chave em pelo menos uma das várias definições de uma classe ou estrutura, mas é recomendável que você usá\-lo em todas as definições parciais.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40046  
  
### Para corrigir este erro  
  
-   Use o [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial) palavra\-chave em cada definição parcial da classe ou estrutura.  
  
## Consulte também  
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)