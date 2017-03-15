---
title: "CA1708: os identificadores devem ser diferentes al&#233;m de mai&#250;sculas de min&#250;sculas | Microsoft Docs"
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
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1708: os identificadores devem ser diferentes al&#233;m de mai&#250;sculas de min&#250;sculas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Os nomes de dois tipos, membros, de parâmetros, ou de namespaces totalmente qualificados forem idênticos quando são convertidos em minúsculas.  
  
## Descrição da Regra  
 Os identificadores de namespaces, tipos, membros, e parâmetros não podem diferir somente por casos como os idiomas que visam Common Language Runtime não é necessário fazer diferenciação de maiúsculas e minúsculas.  Por exemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] é uma linguagem sem diferenciação de maiúsculas e minúsculas amplamente utilizado.  
  
 Esta regra é acionado em membros publicamente visíveis apenas.  
  
## Como Corrigir Violações  
 Selecione um nome que seja exclusivo quando comparado a outros identificadores em um modo sem diferenciação de maiúsculas e minúsculas.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  A biblioteca não pode ser útil em todos os idiomas disponíveis em [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Exemplo de uma Violação  
 O exemplo a seguir demonstra uma violação desta regra.  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## Regras Relacionadas  
 [CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)