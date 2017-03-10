---
title: "CA1035: as implementa&#231;&#245;es de ICollection t&#234;m membros fortemente tipados | Microsoft Docs"
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
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1035: as implementa&#231;&#245;es de ICollection t&#234;m membros fortemente tipados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um implementa protegidos <xref:System.Collections.ICollection?displayProperty=fullName> do tipo mas não oferecem um método com rigidez para <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>.  A versão com rigidez de <xref:System.Collections.ICollection.CopyTo%2A> deve aceitar dois parâmetros e não pode ter <xref:System.Array?displayProperty=fullName> ou uma matriz de <xref:System.Object?displayProperty=fullName> como o primeiro parâmetro.  
  
## Descrição da Regra  
 Essa regra requer implementações de <xref:System.Collections.ICollection> fornecer membros fortemente tipados de forma que usuários não sejam necessários lançar argumentos para o tipo de <xref:System.Object> quando usarem a funcionalidade fornecida pela interface.  Esta regra assumirá que o tipo que implementa <xref:System.Collections.ICollection> fazer isso para gerenciar uma coleção de instâncias de um tipo que é mais segura que <xref:System.Object>.  
  
 <xref:System.Collections.ICollection> implementa a interface de <xref:System.Collections.IEnumerable?displayProperty=fullName> .  Se os objetos da coleção <xref:System.ValueType?displayProperty=fullName>estendem, você deve fornecer um membro com rigidez para que <xref:System.Collections.IEnumerable.GetEnumerator%2A> evite a redução de desempenho que é causado encaixotando.  Isso não é necessário quando os objetos da coleção é um tipo de referência.  
  
 Para implementar uma versão com rigidez de um membro da interface, implemente os membros da interface explicitamente usando nomes no formulário `InterfaceName.InterfaceMemberName`, como <xref:System.Collections.ICollection.CopyTo%2A>.  Os membros explícitos da interface usam os tipos de dados que são declaradas pela interface.  Implementar os membros fortemente tipados usando o nome do membro da interface, como <xref:System.Collections.ICollection.CopyTo%2A>.  Declare os membros fortemente tipados como o utilitário, e declarar os parâmetros e valores de retorno do tipo forte que é gerenciado pela coleção.  Os tipos fortes substituem os tipos mais importantes como <xref:System.Object> e <xref:System.Array> que foram declarados pela interface.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente o membro da interface explicitamente \(a declarar como <xref:System.Collections.ICollection.CopyTo%2A>\).  Adicionar membro com rigidez do utilitário, declarado como `CopyTo`, e mande\-o executar uma matriz com rigidez como o primeiro parâmetro.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se você implementa uma nova coleção de objetos com base, como uma árvore binária, onde os tipos que estendem a nova coleção determinem o tipo forte.  Esses tipos devem estar de acordo com essa regra e expor os membros fortemente tipados.  
  
## Exemplo  
 O exemplo a seguir demonstra a forma correta de implementar <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## Regras Relacionadas  
 [CA1038: os enumeradores devem ser fortemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: as listas são fortemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Consulte também  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>