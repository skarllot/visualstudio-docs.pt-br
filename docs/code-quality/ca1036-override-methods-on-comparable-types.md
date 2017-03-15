---
title: "CA1036: substituir m&#233;todos em tipos compar&#225;veis | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036: substituir m&#233;todos em tipos compar&#225;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um público ou um tipo protegido implementam a interface de <xref:System.IComparable?displayProperty=fullName> e não substitui <xref:System.Object.Equals%2A?displayProperty=fullName> nem sobrecarregam o operador específico do idioma para igualdade, desigualdade, menor que, ou maior que.  A regra não informa uma violação se o tipo herda apenas uma implementação da interface.  
  
## Descrição da Regra  
 Define um tipo que implementam personalizado da ordem de classificação a interface de <xref:System.IComparable> .  O método de <xref:System.IComparable.CompareTo%2A> retorna um valor inteiro que indica a ordem de classificação correta para duas instâncias do tipo.  Esta regra identificará os tipos que definem uma ordem de classificação; isso significa que o significado comum de igualdade, desigualdade, menor que, e maior do que não se apliquem.  Quando você fornece uma implementação de <xref:System.IComparable>em geral, você deve também substituir <xref:System.Object.Equals%2A> de modo que retorna os valores que são consistentes com <xref:System.IComparable.CompareTo%2A>.  Se você substituir <xref:System.Object.Equals%2A> e o está codificando em um idioma com suporte sobrecargas do operador, você também deve fornecer os operadores que são consistentes com <xref:System.Object.Equals%2A>.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua <xref:System.Object.Equals%2A>.  Se a linguagem de programação da suporte ao sobrecarregamento de operador, forneça os seguintes operadores:  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 No C\#, os tokens que são usados para representar esses operadores são os seguintes: \=\=\! \= \<, e \>.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando a violação é causada por operadores ausentes e a linguagem de programação não oferece suporte ao sobrecarregamento de operador, como é o caso com o Visual Basic .NET.  Também é seguro para suprimir um aviso desta regra quando é acionado em operadores de igualdade diferentes de op\_Equality se você verificar que implementa os operadores não faz sentido no contexto do aplicativo.  Porém, você deve sempre sobre o op\_Equality e o operador \=\= se você substituir Object.Equals.  
  
## Exemplo  
 O exemplo a seguir contém um tipo que implementa <xref:System.IComparable>corretamente.  Os comentários de código identificam os métodos que satisfazem as várias regras relacionadas a <xref:System.Object.Equals%2A> e a interface de <xref:System.IComparable> .  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## Exemplo  
 O aplicativo seguir testa o comportamento da implementação de <xref:System.IComparable> que foi mostrada anteriormente.  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## Consulte também  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operadores de igualdade](../Topic/Equality%20Operators.md)