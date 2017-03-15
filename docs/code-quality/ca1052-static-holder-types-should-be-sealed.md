---
title: "CA1052: os tipos de suporte est&#225;tico devem ser lacrados | Microsoft Docs"
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
  - "StaticHolderTypesShouldBeSealed"
  - "CA1052"
helpviewer_keywords: 
  - "CA1052"
  - "StaticHolderTypesShouldBeSealed"
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1052: os tipos de suporte est&#225;tico devem ser lacrados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo protegido contêm apenas membros estáticos e não são declarados com o modificador de [sealed](/dotnet/csharp/language-reference/keywords/sealed) \([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)\).  
  
## Descrição da Regra  
 Esta regra supõe que um tipo que contém apenas membros estáticos não é criado para ser herdado, como o tipo não fornece nenhuma funcionalidade que pode ser substituída em um tipo derivado.  Um tipo que não é significado ser herdado deve ser marcado com o modificador de `sealed` para impedir seu uso como um tipo de base.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o tipo como `sealed`.  Se você estiver destino [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2,0 ou menos, uma abordagem melhor é marcar o tipo como `static`.  Assim, você evita a necessidade de declarar um construtor particular para impedir que a classe foi criada.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra somente se o tipo é projetado para ser herdado.  A ausência de modificador de `sealed` sugere que o tipo é útil como um tipo de base.  
  
## Exemplo de uma Violação  
  
### Descrição  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
### Código  
 [!code-cs[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## Correção com o modificador estático  
  
### Descrição  
 O exemplo a seguir mostra como corrigir uma violação desta regra marcando o tipo com o modificador de `static` .  
  
### Código  
 [!code-cs[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## Regras Relacionadas  
 [CA1053: os tipos de suporte estático não devem ter construtores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)