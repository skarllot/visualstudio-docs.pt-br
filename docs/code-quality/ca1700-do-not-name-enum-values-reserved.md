---
title: "CA1700: n&#227;o nomeie valores de enum como &#39;Reservados&#39; | Microsoft Docs"
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
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1700: n&#227;o nomeie valores de enum como &#39;Reservados&#39;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|CheckId|CA1700|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O nome de um membro da enumeração contém as palavras “reservadas”.  
  
## Descrição da Regra  
 Esta regra pressupõe que um membro da enumeração que tenha um nome que contém “reservado” não é usado atualmente mas é um espaço reservado a ser renomeado ou removido em uma versão futura.  Renomear ou remover um membro é uma alteração.  Você não deve esperar que os usuários para ignorar um membro da mesma forma como o nome contiver “reservadas”, nem pode confiar em usuários para ler ou habitar pela documentação.  Além disso, como os membros reservados aparecem em pesquisadores de objetos e em ambientes de desenvolvimento integrado inteligente, podem causar confusão na qual os membros estão sendo usados de fato.  
  
 Em vez de usar um membro reservado, adicionar um novo membro na versão de enumeração no futuro.  Na maioria dos casos a adição do novo membro não é uma alteração, como a adição não faz os valores dos membros originais à alteração.  
  
 Em um número limitado de casos a adição de um membro é uma alteração até mesmo quando os membros originais retêm seus valores originais.  Primeiro, o novo membro não pode ser retornado dos caminhos existentes do código sem afetar os chamadores que usam uma instrução de `switch` \(`Select` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) no valor de retorno que abrangem a lista do membro e que gerará uma exceção em casos padrão.  Uma preocupação secundário é que o código de cliente não poderia controlar a alteração no comportamento dos métodos de reflexão como <xref:System.Enum.IsDefined%2A?displayProperty=fullName>.  Consequentemente, se o novo membro tem que ser retornado dos métodos existentes ou uma incompatibilidade conhecida do aplicativo ocorre devido ao uso precária de reflexão, a única solução incondicional é:  
  
1.  Adicione uma nova enumeração que contém os membros originais e novos.  
  
2.  Marcar a enumeração original com o atributo de <xref:System.ObsoleteAttribute?displayProperty=fullName> .  
  
 Siga o mesmo procedimento para todos os tipos ou membros visíveis externamente que expõe a enumeração original.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remover ou renomear o membro.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra para um membro que foi usado no momento ou para as bibliotecas que têm enviado anteriormente.  
  
## Regras Relacionadas  
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: não use valores enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: o armazenamento de enum deve ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: os enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)