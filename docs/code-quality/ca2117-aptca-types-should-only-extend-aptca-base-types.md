---
title: "CA2117: os tipos APTCA s&#243; devem estender tipos base APTCA | Microsoft Docs"
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
  - "CA2117"
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
helpviewer_keywords: 
  - "AptcaTypesShouldOnlyExtendAptcaBaseTypes"
  - "CA2117"
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2117: os tipos APTCA s&#243; devem estender tipos base APTCA
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou protegido em um assembly com o atributo de <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> herda de um tipo declarado em um assembly que não tenha o atributo.  
  
## Descrição da Regra  
 Por padrão, o utilitário ou protegido digitar os assemblies com nomes fortes é protegido em implicitamente por [Inheritance Demands](http://msdn.microsoft.com/pt-br/28b9adbb-8f08-4f10-b856-dbf59eb932d9) para o modo confiança total.  Os assemblies de nome forte marcados com o atributo de <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) não têm essa proteção.  O atributo desabilita a procura de herança.  Isso torna os tipos expostos declarados no assembly herdável por tipos que não tem a confiança total.  
  
 Quando o atributo de APTCA presentes em um assembly totalmente confiável, e um tipo no assembly é herdada de um tipo que não permitir chamadores parcialmente confiáveis, uma exploração de segurança é possível.  Se dois tipos `T1` e `T2` atendem às condições a seguir, os chamadores mal\-intencionados podem usar o tipo `T1` para ignorar a procura implícita de herança de confiança total que protege `T2`:  
  
-   `T1` é um tipo público declarado em um assembly totalmente confiável que tem o atributo de APTCA.  
  
-   `T1` herda de um tipo `T2` fora do assembly.  
  
-   o assembly de`T2` não tenha um atributo de APTCA e, consequentemente, não deve ser herdável digitar pelos assemblies parcialmente confiáveis.  
  
 Um tipo parcialmente confiável `X` pode herdar de `T1`, que fornece acesso a membros herdados declarados em `T2`.  Como `T2` não tenha um atributo de APTCA, seu tipo derivado imediato \(`T1`\) deve satisfazer uma procura de herança para o modo confiança total; `T1` tem a confiança total e os como consequência essa verificação.  O risco de segurança é porque participa de `X` não atender à procura de herança que protege `T2` de subclassing não confiável.  Por esse motivo, os tipos com o atributo de APTCA não devem estender os tipos que não têm o atributo.  
  
 Outra problema de segurança, e talvez mais comuns, que são o tipo derivado \(\) pode`T1`, com o erro do programador, membros protegidos exposição do tipo que requer a confiança total \(`T2`\).  Quando isso ocorre, os chamadores não confiáveis obtiverem acesso a informações que deve estar disponível apenas para tipos totalmente confiável.  
  
## Como Corrigir Violações  
 Se o tipo relatado pela violação estiver em um assembly que não requer o atributo de APTCA, exclua\-o.  
  
 Se o atributo de APTCA é necessário, adicione uma procura de herança para o modo confiança total para o tipo.  Isso protege contra a herança por tipos não confiáveis.  
  
 É possível corrigir uma violação adicionando o atributo de APTCA a assemblies dos tipos de base relatados pela violação.  Não faça isto sem primeiro realizar uma análise de segurança intensiva de todo o código em assemblies e de qualquer código que depende dos assemblies.  
  
## Quando Suprimir Alertas  
 Para suprimir com segurança um aviso desta regra, você deve assegurar que os membros protegidos expostas por seu tipo não permitam direta ou indiretamente quais os chamadores não confiáveis acessem informações confidenciais, as operações, ou recursos que podem ser usados em uma forma destrutiva.  
  
## Exemplo  
 O exemplo a seguir usa dois assemblies e um aplicativo de teste para ilustrar a vulnerabilidade de segurança detectada por esta regra.  O primeiro assembly não tenha um atributo de APTCA e não deve ser herdável por tipos parcialmente confiável \(representados por `T2` na discussão anterior\).  
  
 [!code-cs[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## Exemplo  
 O segundo assembly, representado por `T1` na discussão anterior, está totalmente confiável e permitir chamadores parcialmente confiáveis.  
  
 [!CODE [FxCop.Security.YesAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit#1)]  
  
## Exemplo  
 O tipo de teste, representado por `X` na discussão anterior, está em um assembly parcialmente confiável.  
  
 [!CODE [FxCop.Security.TestAptcaInherit#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit#1)]  
  
 O exemplo produz a seguinte saída.  
  
  **Atendem em vale obscuro 2\/22\/2003 de 12:00: 00 AM\!**  
**De teste: prado ensolarado**  
**Atendem em prado ensolarado 2\/22\/2003 de 12:00: 00 AM\!**   
## Regras Relacionadas  
 [CA2116: os métodos APTCA só devem chamar métodos APTCA](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)  
  
## Consulte também  
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)   
 [.NET Framework Assemblies Callable by Partially Trusted Code](http://msdn.microsoft.com/pt-br/a417fcd4-d3ca-4884-a308-3a1a080eac8d)   
 [Usando bibliotecas de código parcialmente confiável](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Inheritance Demands](http://msdn.microsoft.com/pt-br/28b9adbb-8f08-4f10-b856-dbf59eb932d9)