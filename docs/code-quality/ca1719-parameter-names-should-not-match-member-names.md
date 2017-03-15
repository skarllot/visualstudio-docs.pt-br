---
title: "CA1719: os nomes de par&#226;metro n&#227;o devem corresponder aos nomes de membro | Microsoft Docs"
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
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1719: os nomes de par&#226;metro n&#227;o devem corresponder aos nomes de membro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O nome de um membro externamente visível correspondência, em uma comparação sem diferenciação de maiúsculas e minúsculas, o nome de um de seus parâmetros.  
  
## Descrição da Regra  
 Um nome de parâmetro deve comunicar o significado de parâmetro e um nome de membro deve comunicar o significado de um membro.  Seria um design raro onde esses são os mesmos.  Nomeando um parâmetro da mesma forma como o nome do membro é unintuitive e faz a biblioteca difícil usar.  
  
## Como Corrigir Violações  
 Selecione um nome de parâmetro que não corresponde ao nome do membro.  
  
## Quando Suprimir Alertas  
 Para desenvolvimento, nenhum cenário conhecido ocorre quando você precisar eliminar um aviso desta regra.  Para enviar bibliotecas, você pode precisar eliminar um aviso desta regra.  
  
## Regras Relacionadas  
 [CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)