---
title: "CA1716: os identificadores n&#227;o devem corresponder a palavras-chave | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1716: os identificadores n&#227;o devem corresponder a palavras-chave
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um nome de um namespace, de um tipo, ou um membro viritual ou da interface corresponda a uma palavra\-chave reservada em uma linguagem de programação.  
  
## Descrição da Regra  
 Os identificadores de namespaces, tipos e membros virtuais e da interface não devem corresponder às palavras\-chave que são definidos pelos idiomas que visam Common Language Runtime.  Dependendo do idioma usado e a palavra\-chave, os erros e as ambiguidades do compilador pode fazer a biblioteca difícil usar.  
  
 Esta regra verifica em relação a palavra\-chave nos seguintes idiomas:  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 A comparação sem diferenciação de maiúsculas e minúsculas é usada para palavras\-chave de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , e a comparação com diferenciação de maiúsculas e minúsculas é usada para os outros idiomas.  
  
## Como Corrigir Violações  
 Selecione um nome que não aparece na lista de palavras\-chave.  
  
## Quando Suprimir Alertas  
 Você pode suprimir um aviso dessa regra se você for convencido que o identificador não será ofuscado por usuários de API, e que a biblioteca é útil em todos os idiomas disponíveis em [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].