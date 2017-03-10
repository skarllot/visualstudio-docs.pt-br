---
title: "CA1065: n&#227;o acione exce&#231;&#245;es em locais inesperados | Microsoft Docs"
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
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1065: n&#227;o acione exce&#231;&#245;es em locais inesperados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um método que não é esperado que gera de exceções uma exceção.  
  
## Descrição da Regra  
 Os métodos que não são esperados lançar exceções podem ser categorizados como segue:  
  
-   Obtém A propriedade métodos  
  
-   Métodos de acessador de evento  
  
-   Métodos de igual  
  
-   Métodos de GetHashCode  
  
-   Métodos ToString  
  
-   Construtores estáticos  
  
-   Finalizers  
  
-   Disponha métodos  
  
-   Operadores de igualdade  
  
-   Operadores de conversão implícita  
  
 As seções a seguir discutem esses tipos do método.  
  
### Obtém A propriedade métodos  
 As propriedades são campos basicamente inteligente.  Em virtude disso, devem se comportar como um campo o máximo possível.  Os campos não lançam exceções e nenhuma se as propriedades.  Se você tiver uma propriedade que gerou uma exceção, considere torná\-lo um método.  
  
 As seguintes exceções podem ser geradas de uma propriedade obtém o método:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> e todos os derivados \(inclusive <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> e todos os derivadas  
  
-   <xref:System.ArgumentException?displayProperty=fullName> \(somente de indexado obter\)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException> \(somente de indexado obter\)  
  
### Métodos de acessador de evento  
 Os acessadores de evento devem ser as operações simples que não lançam exceções.  Um evento não deve lançar uma exceção quando você tenta adicionar ou remover um manipulador de eventos.  
  
 As seguintes exceções podem ser geradas de um accesor de evento:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> e todos os derivados \(inclusive <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> e todos os derivadas  
  
-   <xref:System.ArgumentException> e derivadas  
  
### Métodos de igual  
 Os seguintes métodos de **Igual a** não deve lançar exceções:  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M: IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 Um método de **Igual a** deve retornar `true` ou `false` em vez de gerar uma exceção.  Por exemplo, se for igual são passados dois tipos incompatíveis deve retornar apenas `false` em vez de gerar <xref:System.ArgumentException>.  
  
### Métodos de GetHashCode  
 Os seguintes métodos de **GetHashCode** não devem normalmente deve lançar exceções:  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M: IEqualityComparer.GetHashCode \(T\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** sempre deve retornar um valor.  Se não, você pode perder itens na tabela de hash.  
  
 As versões de **GetHashCode** que possuem um argumento pode gerar <xref:System.ArgumentException>.  No entanto, **Object.GetHashCode** nunca deve gerar uma exceção.  
  
### Métodos ToString  
 O usa <xref:System.Object.ToString%2A?displayProperty=fullName> do depurador ajudar a exibir informações sobre objetos em formato de cadeia de caracteres.  Consequentemente, **ToString** não deve alterar o estado de um objeto e não deve lançar exceções.  
  
### Construtores estáticos  
 Lançar exceções de um construtor estática faz com que o tipo é inutilizável no domínio de aplicativo atual.  Você deve ter uma boa razão muito \(como um problema de segurança\) para gerar uma exceção de um construtor estático.  
  
### Finalizers  
 Gerar uma exceção de um finalizador CLR causará a falha rapidamente, que rasga para baixo o processo.  Em virtude disso, as exceções de reprodução em um finalizador sempre devem ser evitadas.  
  
### Disponha métodos  
 Um método de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> não deve gerar uma exceção.  Dispose é chamada frequentemente como parte da lógica de acordo com uma cláusula de `finally` .  Consequentemente, gerando uma exceção explicitamente descartado de força o usuário adiciona a manipulação de exceção na cláusula FROM de `finally` .  
  
 O caminho de código de **Descartado \(false\)** nunca deve lançar exceções, pois isso é chamado de quase sempre de um finalizador.  
  
### Operadores de igualdade \(\=\=\! \=\)  
 Como métodos de igual, os operadores de igualdade devem retornar `true` ou `false` e não deve lançar exceções.  
  
### Operadores de conversão implícita  
 Porque o usuário é frequentemente sabe que um operador de conversão implícita esteve chamado, uma exceção lançada pelo operador cast implícita é completamente inesperada.  Consequentemente, nenhuma exceção deve ser gerada de operadores de conversão implícita.  
  
## Como Corrigir Violações  
 Para getter de propriedade, qualquer alteração a lógica de forma que não mais tenha que lance uma exceção, ou alterar a propriedade de um método.  
  
 Para todos os outros tipos de método listados anteriormente, altere a lógica de modo que já não precisa gerar uma exceção.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se a violação foi causado por uma declaração de exceção em vez de uma exceção gerada.  
  
## Regras Relacionadas  
 [CA2219: não acione exceções em cláusulas de exceção](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)  
  
## Consulte também  
 [Avisos de design](../code-quality/design-warnings.md)