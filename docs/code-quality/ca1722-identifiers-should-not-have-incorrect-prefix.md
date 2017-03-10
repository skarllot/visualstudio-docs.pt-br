---
title: "CA1722: os identificadores n&#227;o devem ter prefixo incorreto | Microsoft Docs"
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
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1722: os identificadores n&#227;o devem ter prefixo incorreto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um identificador tem mais um prefixo incorreto.  
  
## Descrição da Regra  
 Por convenção, somente determinados elementos de programação têm nomes que começam com um prefixo específico.  
  
 Os nomes de tipo não têm um prefixo específico e não devem ser precedidos por C “2.0”.  Esta regra relata violações para nomes de tipo como “CMyClass” e não relata violações para nomes de tipo como “cache”.  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
## Como Corrigir Violações  
 Remova o prefixo do identificador.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Regras Relacionadas  
 [CA1715: os identificadores devem ter o prefixo correto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)