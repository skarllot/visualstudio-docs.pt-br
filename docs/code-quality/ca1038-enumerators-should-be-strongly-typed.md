---
title: "CA1038: os enumeradores devem ser fortemente tipados | Microsoft Docs"
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
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1038: os enumeradores devem ser fortemente tipados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um implementa protegidos <xref:System.Collections.IEnumerator?displayProperty=fullName> do tipo mas não fornecem uma versão com rigidez da propriedade de <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> .  Tipos que é derivada dos seguintes tipos é isento dessa regra:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## Descrição da Regra  
 Essa regra requer implementações de <xref:System.Collections.IEnumerator> fornecer também uma versão com rigidez da propriedade de <xref:System.Collections.IEnumerator.Current%2A> de forma que usuários não sejam necessários para converter o valor de retorno no tipo forte quando usarem a funcionalidade fornecida pela interface.  Esta regra assumirá que o tipo que implementa <xref:System.Collections.IEnumerator> contém uma coleção de instâncias de um tipo que é mais segura que <xref:System.Object>.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente a propriedade da interface explicitamente \(a declarar como `IEnumerator.Current`\).  Adicionar uma versão com rigidez do utilitário a propriedade, declarada como `Current`, e mande\-a retornar um objeto com rigidez.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra quando você implementa um enumerador baseado em objeto para uso com uma coleção de objetos com base, como uma árvore binária.  Tipos que estende a nova coleção definirá o enumerador com rigidez e expõe a propriedade com rigidez de tipos.  
  
## Exemplo  
 O exemplo a seguir demonstra a forma correta da implementação de um tipo com rigidez de <xref:System.Collections.IEnumerator> .  
  
 [!CODE [FxCop.Design.IEnumeratorStrongTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes#1)]  
  
## Regras Relacionadas  
 [CA1035: as implementações de ICollection têm membros fortemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: as listas são fortemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Consulte também  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>