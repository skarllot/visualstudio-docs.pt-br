---
title: "CA1715: os identificadores devem ter o prefixo correto | Microsoft Docs"
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
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1715: os identificadores devem ter o prefixo correto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Interromper \- quando é acionado em interfaces.<br /><br /> Sem\-quebras \- se for gerado em parâmetros de tipo genéricas.|  
  
## Causa  
 O nome de uma interface visível não externamente me começa com maiúscula “”.  
  
 \- ou \-  
  
 O nome de um parâmetro de tipo genérico em um tipo ou um método externamente visível não começa com um “T” maiúsculo.  
  
## Descrição da Regra  
 Por convenção, os nomes de determinado início dos elementos de programação com um prefixo específico.  
  
 Os nomes da interface devem começar\-me com maiúscula “” seguido por outra letra maiúscula.  Esta regra relata violações para nomes da interface como “MyInterface” e “IsolatedInterface”.  
  
 Os nomes de parâmetro de tipo genéricas devem começar com um “T” maiúsculo e opcionalmente podem ser seguido por outra letra maiúscula.  Esta regra relata violações para nomes de parâmetro de tipo genéricas como “V” e “tipo”.  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
## Como Corrigir Violações  
 Renomeie o identificador de modo que é prefixado corretamente.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 **O exemplo a seguir mostra uma interface incorretamente denominada.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## Exemplo  
 **O exemplo a seguir corrige a violação anterior para prefixar a interface com “i”.**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## Exemplo  
 **O exemplo a seguir mostra um parâmetro de tipo genérico nomeado incorretamente.**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1)]  
  
## Exemplo  
 **O exemplo a seguir corrige a violação anterior para prefixar o parâmetro de tipo genérico com “T”.**  
  
 [!CODE [FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1)]  
  
## Regras Relacionadas  
 [CA1722: os identificadores não devem ter prefixo incorreto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)