---
title: "CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta | Microsoft Docs"
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
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1703: as cadeias de caracteres do recurso devem ter a ortografia correta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Uma cadeia de caracteres de recurso contém uma ou mais palavras que não são reconhecidos pela biblioteca de SPELLING CHECKER da Microsoft.  
  
## Descrição da Regra  
 Esta regra analisa a cadeia de caracteres de recurso em palavras \(palavras compostas de geração de tokens\) e em verificações a ortografia de cada palavra\/token.  Para obter informações sobre o algoritmo de análise, consulte [CA1704: os identificadores do recurso devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Por padrão, a versão em inglês \(en\) de SPELLING CHECKER é usada.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, palavras completas de uso que corretamente por estar escrito ou adicionam palavras a um dicionário personalizado.  Para obter informações sobre como usar dicionários personalizados, consulte [CA1704: os identificadores do recurso devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  As palavras estar escrito corretamente reduzem o tempo necessário para obter novas bibliotecas de software.  
  
## Regras Relacionadas  
 [CA1701: as palavras compostas da cadeia de caracteres do recurso devem ter maiúsculas e minúsculas corretas](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)  
  
 [CA1704: os identificadores do recurso devem ter a ortografia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: os literais do recurso devem ter a ortografia correta](../code-quality/ca2204-literals-should-be-spelled-correctly.md)