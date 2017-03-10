---
title: "CA2119: os m&#233;todos para lacrar que atendam a interfaces privadas | Microsoft Docs"
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
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2119: os m&#233;todos para lacrar que atendam a interfaces privadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo herdável utilitário fornece uma implementação substituível do método de uma interface de `internal` \(`Friend` no Visual Basic\).  
  
## Descrição da Regra  
 Os métodos da interface têm acessibilidade pública, que não pode ser alterada pelo tipo de implementação.  Uma interface interna cria um contrato que não deve ser implementado fora do assembly que define a interface.  Um tipo utilitário que implementa um método de uma interface interna usando o modificador de `virtual` \(`Overridable` no Visual Basic\) permite que o método foi substituído por um tipo derivado que está fora do assembly.  Se um segundo no assembly de definição chama o método e aguarda um contrato interno somente leitura, comportamento poderia ser afetado quando, em vez disso, o método substituído no assembly externo é executado.  Isso cria uma vulnerabilidade de segurança.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, evitar o método de ser substituído fora do assembly usando um dos seguintes:  
  
-   Faça o tipo declarando `sealed` \(`NotInheritable` no Visual Basic\).  
  
-   Alterar a acessibilidade do tipo declarando a `internal` \(`Friend` no Visual Basic\).  
  
-   Remover todos os construtores públicos do tipo declarando.  
  
-   Implementar o método sem usar o modificador de `virtual` .  
  
-   Implementar o método explicitamente.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se, depois de revisar cuidado, nenhuma problemas de segurança existentes que podem ser exploráveis se o método for substituído fora do assembly.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo, `BaseImplementation`, que viola esta regra.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## Exemplo  
 O exemplo a seguir explorar a implementação do método virtual do exemplo anterior.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## Consulte também  
 [Interfaces](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)