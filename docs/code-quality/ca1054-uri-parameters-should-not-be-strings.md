---
title: "CA1054: os par&#226;metros de URI n&#227;o devem ser cadeias de caracteres | Microsoft Docs"
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
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1054: os par&#226;metros de URI n&#227;o devem ser cadeias de caracteres
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|CheckId|CA1054|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo declara um método com um parâmetro de cadeia de caracteres cujo nome contém “uri”, “Um”, “urn”, “urn”, “URL”, ou “URL” e o tipo não declarem uma sobrecarga correspondente que usa um parâmetro de <xref:System.Uri?displayProperty=fullName> .  
  
## Descrição da Regra  
 Essa regra se divide o nome do parâmetro em tokens com base na convenção de uso de maiúsculas e minúsculas em camelo e verifique se cada token é igual a “uri”, “Uri”, “urn”, “urn”, “URL”, ou “URL”.  Se houver uma correspondência, a regra supõe que o parâmetro representa o Uniform Resource Identifier \(URI\).  Uma representação de cadeia de caracteres de um URI for susceptível a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança.  Se um método usa uma representação de cadeia de caracteres de um URI, uma sobrecarga correspondente deve ser contanto que usa uma instância da classe de <xref:System.Uri> , que fornece estes serviços em um cofre e uma maneira segura.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o parâmetro em um tipo de <xref:System.Uri> ; essa é uma alteração.  Opcionalmente, forneça uma sobrecarga do método que assume um parâmetro de <xref:System.Uri> ; essa é uma alteração incondicional.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o parâmetro não representa um URI.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo, `ErrorProne`, que viola essa regra, e um tipo, `SaferWay`, que satisfaça a regra.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## Regras Relacionadas  
 [CA1056: as propriedades de URI não devem ser cadeias de caracteres](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: os valores de retorno de URI não devem ser cadeias de caracteres](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: passar objetos System.Uri em vez de cadeias de caracteres](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)  
  
 [CA1057: as sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)