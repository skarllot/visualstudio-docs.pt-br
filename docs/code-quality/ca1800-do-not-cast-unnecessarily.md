---
title: "CA1800: n&#227;o converter desnecessariamente | Microsoft Docs"
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
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1800: n&#227;o converter desnecessariamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método executa conversões duplicados em um de seus argumentos ou variáveis locais.  Para a análise completa por esta regra, o assembly testado deve ser criado usando informações de depuração e o arquivo associado de base de dados do programa \(.pdb\) deve estar disponível.  
  
## Descrição da Regra  
 As conversões duplicados diminui o desempenho, principalmente quando as conversões são executadas em instruções compactas da iteração.  Para operações de conversão explícitas duplicados, armazenar o resultado da conversão em uma variável local e usar variável local em vez das operações de conversão duplicados.  
  
 Se o operador C\# `is` é usado para testar se a conversão for bem\-sucedida antes que a conversão real seja executada, considere testar o resultado do operador de `as` em vez disso.  Isso fornece a mesma funcionalidade sem a operação de conversão implícita é executada pelo operador de `is` .  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, modifique a implementação do método para minimizar o número de operações de conversão.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra, ou ignorar completamente a regra, se o desempenho não é um problema.  
  
## Exemplo  
 O exemplo a seguir mostra um método que viola a regra usando o operador C\# `is` .  Um segundo método obedece à regra substituindo o operador de `is` com um teste no resultado do operador de `as` , que diminui o número de operações de conversão pela iteração de dois a uma.  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra um método, `start_Click`, que tem conversões explícitas duplicados de múltiplas, que viola a regra, e um método, `reset_Click`, que satisfaça a regra para armazenar a conversão em uma variável local.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## Consulte também  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)