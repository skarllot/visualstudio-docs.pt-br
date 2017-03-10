---
title: "CA2104: n&#227;o declarar tipos de refer&#234;ncia mut&#225;veis somente leitura | Microsoft Docs"
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
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2104: n&#227;o declarar tipos de refer&#234;ncia mut&#225;veis somente leitura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo externamente visível contém um campo somente leitura externamente visível que é um tipo mutável de referência.  
  
## Descrição da Regra  
 Um tipo mutável é um tipo cujos dados da instância sejam modificadas.  A classe de <xref:System.Text.StringBuilder?displayProperty=fullName> é um exemplo de um tipo mutável de referência.  Contém membros que podem alterar o valor de uma instância da classe.  Um exemplo de um imutável tipo de referência é a classe de <xref:System.String?displayProperty=fullName> .  Depois que foi criado uma instância do, seu valor nunca pode ser alterado.  
  
 O modificador somente leitura \([readonly](/dotnet/csharp/language-reference/keywords/readonly) no C\#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], e [const](/visual-cpp/cpp/const-cpp) em C\+\+\) em um campo do tipo de referência \(ponteiro em C\+\+\) evitam que o campo seja substituído por uma instância diferente do tipo de referência.  Porém, o modificador não impede que os dados da instância do campo sejam alterados por meio do tipo de referência.  
  
 Os campos somente leitura da matriz são isentos desta regra causam mas em vez de uma violação de regra de [CA2105: os campos da matriz não devem ser somente leitura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) .  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o modificador somente leitura ou, se uma alteração for aceitável, substitua o campo com um tipo imutável.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o tipo de campo é imutável.  
  
## Exemplo  
 O exemplo a seguir mostra uma declaração de campo que faz com que uma violação desta regra.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]