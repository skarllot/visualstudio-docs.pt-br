---
title: "CA1057: as sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri | Microsoft Docs"
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
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057: as sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|CheckId|CA1057|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo declara as sobrecargas do método que diferem apenas pela substituição de um parâmetro de cadeia de caracteres com um parâmetro de <xref:System.Uri?displayProperty=fullName> , e a sobrecarga que usa o parâmetro de cadeia de caracteres não chama a sobrecarga que usa o parâmetro de <xref:System.Uri> .  
  
## Descrição da Regra  
 Como as sobrecargas diferem apenas pelo parâmetro de<xref:System.Uri> da corda, a cadeia de caracteres é usada para representar Uniform Resource Identifier \(URI\).  Uma representação de cadeia de caracteres de um URI for susceptível a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança.  A classe de <xref:System.Uri> fornece estes serviços em um cofre e uma maneira segura.  Para coletar os benefícios de <xref:System.Uri> classe, a sobrecarga de cadeia de caracteres deve chamar a sobrecarga de <xref:System.Uri> usando o argumento de cadeia de caracteres.  
  
## Como Corrigir Violações  
 o novo implementar o método que usa a representação de cadeia de caracteres URI de modo que cria uma instância da classe de <xref:System.Uri> que usa o argumento de cadeia de caracteres, e passar o objeto de <xref:System.Uri> a sobrecarga que tem o parâmetro de <xref:System.Uri> .  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o parâmetro de cadeia de caracteres não representa um URI.  
  
## Exemplo  
 O exemplo a seguir mostra uma sobrecarga corretamente implementada de cadeia de caracteres.  
  
 [!CODE [FxCop.Design.CallUriOverload#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload#1)]  
  
## Regras Relacionadas  
 [CA2234: passar objetos System.Uri em vez de cadeias de caracteres](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1056: as propriedades de URI não devem ser cadeias de caracteres](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: os parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: os valores de retorno de URI não devem ser cadeias de caracteres](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)