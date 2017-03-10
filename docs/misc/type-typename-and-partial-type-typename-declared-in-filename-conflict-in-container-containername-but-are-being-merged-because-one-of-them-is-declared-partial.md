---
title: "Tipo &#39;&lt; typename &gt;&#39; e tipo parcial &#39;&lt; typename &gt;&#39; declarado em &#39;&lt; nomedoarquivo &gt;&#39; est&#227;o em conflito no cont&#234;iner &#39;&lt; nomecont&#234;iner &gt;&#39;, mas est&#227;o sendo mesclados porque um deles &#233; declarado parcial | Microsoft Docs"
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
  - "vbc40047"
  - "bc40047"
helpviewer_keywords: 
  - "BC40047"
ms.assetid: 05f62dd9-f97d-4893-8904-76ecd2da474c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo &#39;&lt; typename &gt;&#39; e tipo parcial &#39;&lt; typename &gt;&#39; declarado em &#39;&lt; nomedoarquivo &gt;&#39; est&#227;o em conflito no cont&#234;iner &#39;&lt; nomecont&#234;iner &gt;&#39;, mas est&#227;o sendo mesclados porque um deles &#233; declarado parcial
Uma classe ou estrutura é exibido em várias definições no mesmo tipo de continente, e mais de uma definição não está marcado como `Partial`.  
  
 Você deve usar o [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial) palavra\-chave em pelo menos uma das várias definições de uma classe ou estrutura, mas é recomendável que você usá\-lo em todas as definições parciais.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40047  
  
### Para corrigir este erro  
  
-   Use o [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial) palavra\-chave em cada definição parcial da classe ou estrutura.