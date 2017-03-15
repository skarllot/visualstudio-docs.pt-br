---
title: "CA1021: evitar par&#226;metros de sa&#237;da | Microsoft Docs"
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
  - "CA1021"
  - "AvoidOutParameters"
helpviewer_keywords: 
  - "AvoidOutParameters"
  - "CA1021"
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1021: evitar par&#226;metros de sa&#237;da
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOutParameters|  
|CheckId|CA1021|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um método protegido em um tipo utilitário têm um parâmetro de `out` .  
  
## Descrição da Regra  
 Passar tipos por referência \(usando `out` ou `ref`\) requer experiência com ponteiros, compreender como os tipos de valor e os tipos de referência são diferentes, e os métodos de manipulação com vários valores de retorno.  Além disso, a diferença entre `out` e os parâmetros de `ref` não são compreendidos muito.  
  
 Quando um tipo de referência é passado por referência “,” o método pretende usar o parâmetro para retornar uma instância diferente do objeto.  Passando um tipo de referência por referência também é conhecido como usar um ponteiro vezes, o ponteiro para um ponteiro, ou de nomes indiretos duplo.  Usando a convenção padrão de chamada, que é passagem pelo valor “,” um parâmetro que usa um tipo de referência já recebe um ponteiro para o objeto.  O ponteiro, não ao objeto que aponta, é passado pelo valor.  A passagem pelo valor significa que o método não pode alterar o ponteiro para o que aponte para uma nova instância do tipo de referência.  No entanto, pode modificar o conteúdo do objeto ao qual aponta.  Para a maioria dos aplicativos isso é suficiente e gerencie o comportamento desejado.  
  
 Se um método deve retornar uma instância diferente, use o valor de retorno do método para fazer isso.  Consulte a classe de <xref:System.String?displayProperty=fullName> para uma variedade de métodos que operam em cadeias de caracteres e retornam uma nova instância de uma cadeia de caracteres.  Quando esse modelo é usado, o chamador deve decidir se o objeto original é preservado.  
  
 Embora os valores de retorno são comuns e intensamente usado, o aplicativo correto de `out` e os parâmetros de `ref` exigem habilidades intermediários de design e de codificação.  Os arquitetos de biblioteca que criam para um público geral não devem esperar que os usuários dominar trabalhar com `out` ou parâmetros de `ref` .  
  
## Como Corrigir Violações  
 Para corrigir uma violação dessa regra é causada por um tipo de valor, tem o retorno do método do objeto como seu valor de retorno.  Se o método deve retornar vários valores, remodele\-o para retornar uma única instância de um objeto que contém os valores.  
  
 Para corrigir uma violação dessa regra é causada por um tipo de referência, certifique\-se de que o comportamento desejado é retornar uma nova instância de referência.  Se for, o método deve usar o valor de retorno para fazer isso.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra.  No entanto, esse design pode causar problemas de usabilidade.  
  
## Exemplo  
 A biblioteca seguir mostra duas implementações de uma classe que gerencia respostas aos comentários de um usuário.  A primeira implementação \(`BadRefAndOut`\) força o usuário de biblioteca para gerenciar três valores de retorno.  A segunda implementação \(`RedesignedRefAndOut`\) simplifica a experiência do usuário retornando uma instância de uma classe do contêiner \(`ReplyData`\) que gerencia os dados como uma única unidade.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## Exemplo  
 O aplicativo seguir ilustra a experiência do usuário.  A chamada para a biblioteca alto \(método de`UseTheSimplifiedClass` \) é mais simples, e as informações retornada pelo método é gerenciado facilmente.  A saída dos dois métodos são idênticas.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## Exemplo  
 Biblioteca de exemplo a seguir ilustra como os parâmetros de `ref` para tipos de referência são usados e mostra uma maneira ideal de implementar essa funcionalidade.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## Exemplo  
 O seguinte aplicativo chama cada método na biblioteca para demonstrar o comportamento.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **Alterando o ponteiro \- passado pelo valor:**  
**12345**  
**12345**  
**Alterando o ponteiro \- passado por referência:**  
**12345**  
**12345 ABCDE**  
**Passar pelo valor de retorno:**  
**12345 ABCDE**   
## Métodos de padrão da tentativa  
  
### Descrição  
 Os métodos que implementam o padrão de **Tentativa\<Algo\>** , como <xref:System.Int32.TryParse%2A?displayProperty=fullName>, não lançam essa violação.  O exemplo a seguir mostra uma estrutura \(tipo de valor\) que implementa o método de <xref:System.Int32.TryParse%2A?displayProperty=fullName> .  
  
### Código  
 [!CODE [FxCop.Design.TryPattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern#1)]  
  
## Regras Relacionadas  
 [CA1045: não passar tipos por referência](../code-quality/ca1045-do-not-pass-types-by-reference.md)