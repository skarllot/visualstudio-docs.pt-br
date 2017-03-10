---
title: "CA2112: os tipos seguros n&#227;o devem expor campos | Microsoft Docs"
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
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112: os tipos seguros n&#227;o devem expor campos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo protegido contêm campos públicos e são protegidos por [Demandas de link](../Topic/Link%20Demands.md).  
  
## Descrição da Regra  
 Se o código tenha acesso a uma instância de um tipo que é protegida por uma procura de link, o código não precisa atender à procura de link para acessar os campos do tipo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, torne os campos público e adicionar propriedades públicas ou métodos que retornam dados do campo.  As verificações de segurança de LinkDemand em tipos proteger o acesso às propriedades e os métodos de tipo.  No entanto, a segurança de acesso a código não se aplica aos campos.  
  
## Quando Suprimir Alertas  
 Para problemas de segurança e para o bom design, você deve corrigir violações tornando os campos públicos público.  Você pode suprimir um aviso dessa regra se o campo não mantém as informações que devem permanecer sombreada, e você não confie no conteúdo do campo.  
  
## Exemplo  
 O exemplo é composto de um tipo de biblioteca \(`SecuredTypeWithFields`\) com campos inseguros, de um tipo \(`Distributor`\) que possam criar instâncias do tipo da biblioteca e as instâncias confundidas do para tipos não têm permissão para criar, e o código do aplicativo que pode ler os campos de uma instância mesmo que não tenha a permissão que protege o tipo.  
  
 O código de biblioteca viola a regra.  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## Exemplo  
 O aplicativo não pode criar uma instância do devido à procura de link que protege o tipo seguro.  A seguinte classe permite que o aplicativo obter uma instância do tipo seguro.  
  
 [!CODE [FxCop.Security.LDOnFieldsDistributor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor#1)]  
  
## Exemplo  
 O aplicativo seguir ilustra como, sem permissão para acessar os métodos de um tipo protegido, o código pode acessar seus campos.  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **Criando uma instância de SecuredTypeWithFields.**  
**Campos protegidos de tipo: 22, 33**  
**Alterando o campo de tipo protegido…**  
**Campos armazenados em cachê do objeto: 99, 33**   
## Regras Relacionadas  
 [CA1051: não declarar campos de instância visíveis](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Consulte também  
 [Demandas de link](../Topic/Link%20Demands.md)   
 [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)