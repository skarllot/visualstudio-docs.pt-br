---
title: "CA1502: evitar complexidade excessiva | Microsoft Docs"
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
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1502: evitar complexidade excessiva
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Categoria|Microsoft.Maintainability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método tem uma complexidade cyclomatic excessiva.  
  
## Descrição da Regra  
 *A complexidade de Cyclomatic* ultrapassar o número de caminhos linear independentes com o método, que é determinado pelo número e a complexidade das ramificações anteriores.  Uma baixa complexidade cyclomatic normalmente indica um método que seja fácil de entender, teste, e manter.  A complexidade cyclomatic é calculada de um gráfico de fluxo de controle do método e determinada como segue:  
  
 complexidade cyclomatic \= o número de bordas \- o número de nós \+ 1  
  
 onde um nó representa um ponto de ramificação de lógica e uma borda representam uma linha entre dois nós.  
  
 A regra relata uma violação quando a complexidade cyclomatic for maior que 25.  
  
 Você pode saber mais sobre a métrica de código em [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, refactor o método para reduzir a complexidade cyclomatic.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se a complexidade não pode ser facilmente reduzida e o método é fácil de entender, teste, e manter.  Em particular, um método que contém uma grande instrução de `switch` \(`Select` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) é um candidato para exclusão.  O risco de desestabilizar a base de código tarde no ciclo de desenvolvimento ou de introduzir inesperadamente uma alteração no comportamento de tempo de execução no código fornecido anteriormente pode aumentar os benefícios de manutenibilidade de refactoring o código.  
  
## Como a complexidade de Cyclomatic é calculada  
 A complexidade cyclomatic é calculada somando\-se 1 ao seguinte:  
  
-   Número de ramificações \(como `if`, `while`, e `do`\)  
  
-   Número de instruções `case` em `switch`  
  
 Os seguintes métodos de apresentação dos exemplos que têm complexidades cyclomatic de negócio.  
  
## Exemplo  
 **Complexidade de Cyclomatic de 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## Exemplo  
 **Complexidade de Cyclomatic de 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## Exemplo  
 **Complexidade de Cyclomatic de 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## Exemplo  
 **Complexidade de Cyclomatic de 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## Regras Relacionadas  
 [CA1501: evitar herança excessiva](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## Consulte também  
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)