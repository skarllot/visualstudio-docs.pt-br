---
title: "CA2243: os literais da cadeia de caracteres de atributo devem ser analisados corretamente | Microsoft Docs"
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
  - "CA2243"
  - "AttributeStringLiteralsShouldParseCorrectly"
helpviewer_keywords: 
  - "AttributeStringLiteralsShouldParseCorrectly"
  - "CA2243"
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2243: os literais da cadeia de caracteres de atributo devem ser analisados corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 O parâmetro literal de cadeia de caracteres de um atributo não analisa corretamente para uma URL, GUID, ou a versão.  
  
## Descrição da Regra  
 Como os atributos são derivados de <xref:System.Attribute?displayProperty=fullName>, e os atributos são usados em tempo de compilação, somente valores constantes podem ser passados para seus construtores.  Atribua parâmetros que devem representar URL, GUIDs e as versões não podem ser digitadas como <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, e <xref:System.Version?displayProperty=fullName>, pois esses tipos não podem ser representados como constantes.  Em vez disso, devem ser representados por cadeias de caracteres.  
  
 Porque o parâmetro é digitado como uma cadeia de caracteres, é possível que um parâmetro incorretamente formatado pode ser passado em tempo de compilação.  
  
 Esta regra usa uma nomeação heurística para localizar os parâmetros que representam o Uniform Resource Identifier \(URI\), um GUID \(identificador global exclusivo\) ou uma versão e verifica se o valor passado está correto.  
  
## Como Corrigir Violações  
 Altere a cadeia de caracteres de parâmetro em uma URL corretamente formado, a GUID, ou à versão.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o parâmetro não representa uma URL, GUID, ou a versão.  
  
## Exemplo  
 O código a seguir mostra de exemplo para o AssemblyFileVersionAttribute que viola esta regra.  
  
 [!code-cs[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 A regra é disparada pelo seguinte:  
  
-   Parâmetros que contêm “versão” e não pode ser analisado a System.Version.  
  
-   Parâmetros que contêm “GUID” e não pode ser analisado a System.Guid.  
  
-   Os parâmetros que contêm “uri”, “urn,” ou “URL” e não pode ser analisado a System.Uri.  
  
## Consulte também  
 [CA1054: os parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)