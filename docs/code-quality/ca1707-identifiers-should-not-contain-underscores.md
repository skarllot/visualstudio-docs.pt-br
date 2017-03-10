---
title: "CA1707: os identificadores n&#227;o devem conter sublinhados | Microsoft Docs"
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
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1707: os identificadores n&#227;o devem conter sublinhados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Interromper quando \- gerado em assemblies<br /><br /> Sem\-quebras \- se for gerado em parâmetros de tipo|  
  
## Causa  
 O nome de um identificador contiver o caractere de sublinhado \(\_\).  
  
## Descrição da Regra  
 Por convenção, os nomes de identificadores não contêm o caractere de sublinhado \(\_\).  A regra verifica namespaces, tipos, membros, e parâmetros.  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
## Como Corrigir Violações  
 Remova todos os caracteres sublinhados do nome.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Regras Relacionadas  
 [CA1709: os identificadores do recurso devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)