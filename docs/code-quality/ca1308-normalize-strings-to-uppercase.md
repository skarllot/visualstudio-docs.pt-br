---
title: "CA1308: normalizar cadeias de caracteres para mai&#250;sculas | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1308: normalizar cadeias de caracteres para mai&#250;sculas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Uma operação normaliza uma cadeia de caracteres em minúsculas.  
  
## Descrição da Regra  
 As cadeias de caracteres devem ser normalizadas em maiúsculas.  Um pequeno grupo de caracteres, quando são convertidos em minúsculas, não pode fazer uma viagem de ida e volta.  Para fazer uma viagem de ida e volta significa converter os caracteres de uma localidade para outra localidade que representa dados de caractere diferente, e recuperar exatamente nos caracteres original de caracteres convertidos.  
  
## Como Corrigir Violações  
 Alterar as operações que converte cadeias de caracteres em minúsculas de modo que as cadeias de caracteres são convertidas em maiúsculos em vez disso.  Por exemplo, altere `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## Quando Suprimir Alertas  
 É seguro para suprimir uma mensagem de aviso quando você não está fazendo a decisão da segurança com base no resultado \(por exemplo, quando você o está exibindo na interface do usuário\).  
  
## Consulte também  
 [Avisos de globalização](../code-quality/globalization-warnings.md)