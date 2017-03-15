---
title: "CA1039: as listas s&#227;o fortemente tipadas | Microsoft Docs"
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
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1039: as listas s&#227;o fortemente tipadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O utilitário ou o implementa protegidos <xref:System.Collections.IList?displayProperty=fullName> do tipo mas não oferecem um método com rigidez para um ou mais dos seguintes:  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## Descrição da Regra  
 Essa regra requer implementações de <xref:System.Collections.IList> fornecer membros fortemente tipados de forma que usuários não sejam necessários lançar argumentos para o tipo de <xref:System.Object?displayProperty=fullName> quando usarem a funcionalidade fornecida pela interface.  A interface de <xref:System.Collections.IList> é implementada por coleções de objetos que podem ser acessados pelo índice.  Esta regra assumirá que o tipo que implementa <xref:System.Collections.IList> o faz para gerenciar uma coleção de instâncias de um tipo que é mais segura que <xref:System.Object>.  
  
 <xref:System.Collections.IList> implementa as interfaces de <xref:System.Collections.ICollection?displayProperty=fullName> e de <xref:System.Collections.IEnumerable?displayProperty=fullName> .  Se você implementa <xref:System.Collections.IList>, você deve fornecer os membros fortemente tipados necessários para <xref:System.Collections.ICollection>.  Se os objetos da coleção <xref:System.ValueType?displayProperty=fullName>estendem, você deve fornecer um membro com rigidez para que <xref:System.Collections.IEnumerable.GetEnumerator%2A> evite a redução de desempenho que é causado encaixotando; isso não é necessário quando os objetos da coleção é um tipo de referência.  
  
 Para estar de acordo com essa regra, implementar os membros da interface explicitamente usando nomes no formulário InterfaceName.InterfaceMemberName, como <xref:System.Collections.IList.Add%2A>.  Os membros explícitos da interface usam os tipos de dados que são declaradas pela interface.  Implementar os membros fortemente tipados usando o nome do membro da interface, como `Add`.  Declare os membros fortemente tipados como o utilitário, e declarar os parâmetros e valores de retorno do tipo forte que é gerenciado pela coleção.  Os tipos fortes substituem os tipos mais importantes como <xref:System.Object> e <xref:System.Array> que foram declarados pela interface.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, explicitamente implementar membros de <xref:System.Collections.IList> e fornecer de backup fortemente tipadas para os membros que foram observados anteriormente.  Corretamente para o código que implementa a interface de <xref:System.Collections.IList> e fornece os membros fortemente tipados exigidas, consulte o exemplo.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra quando você implementa uma nova coleção de objetos com base, como uma lista vinculada, onde os tipos que estendem a nova coleção determinem o tipo forte.  Esses tipos devem estar de acordo com essa regra e expor os membros fortemente tipados.  
  
## Exemplo  
 No exemplo a seguir, o tipo `YourType` estende <xref:System.Collections.CollectionBase?displayProperty=fullName>, como eles devem todas as coleções fortemente tipadas.  Observe que <xref:System.Collections.CollectionBase> fornece implementação explícita da interface de <xref:System.Collections.IList> para você.  Em virtude disso, você só deve fornecer os membros com rigidez de tipo para <xref:System.Collections.IList> e <xref:System.Collections.ICollection>.  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## Regras Relacionadas  
 [CA1035: as implementações de ICollection têm membros fortemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038: os enumeradores devem ser fortemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## Consulte também  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>