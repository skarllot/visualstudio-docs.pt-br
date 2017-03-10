---
title: "CA1056: as propriedades de URI n&#227;o devem ser cadeias de caracteres | Microsoft Docs"
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
  - "UriPropertiesShouldNotBeStrings"
  - "CA1056"
helpviewer_keywords: 
  - "CA1056"
  - "UriPropertiesShouldNotBeStrings"
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1056: as propriedades de URI n&#227;o devem ser cadeias de caracteres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriPropertiesShouldNotBeStrings|  
|CheckId|CA1056|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo declara uma propriedade de cadeia de caracteres cujo nome contém “uri”, “Uri”, “urn”, “urn”, “URL”, ou “URL”.  
  
## Descrição da Regra  
 Essa regra se divide o nome da propriedade em tokens com base na convenção de maiúsculas e minúsculas de Pascal e verifique se cada token é igual a “uri”, “Uri”, “urn”, “urn”, “URL”, ou “URL”.  Se houver uma correspondência, a regra supõe que a propriedade representa o Uniform Resource Identifier \(URI\).  Uma representação de cadeia de caracteres de um URI for susceptível a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança.  A classe de <xref:System.Uri?displayProperty=fullName> fornece estes serviços em um cofre e uma maneira segura.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a propriedade para um tipo de <xref:System.Uri> .  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se a propriedade não representa um URI.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo, `ErrorProne`, que viola essa regra, e um tipo, `SaferWay`, que satisfaça a regra.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1056-uri-properties-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1056-uri-properties-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1056-uri-properties-should-not-be-strings_1.cpp)]  
  
## Regras Relacionadas  
 [CA1054: os parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: os valores de retorno de URI não devem ser cadeias de caracteres](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: passar objetos System.Uri em vez de cadeias de caracteres](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: as sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)