---
title: "CA2108: revisar seguran&#231;a declarativa em tipos de valor | Microsoft Docs"
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
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108: revisar seguran&#231;a declarativa em tipos de valor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um público ou um tipo de valor protegido são protegidos por [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) ou por [Demandas de link](../Topic/Link%20Demands.md).  
  
## Descrição da Regra  
 Os tipos de valor são atribuídos e inicializados pelos construtores padrão para que outros construtores executados.  Se um tipo de valor é protegida por uma procurar ou por um LinkDemand, e o chamador não tem as permissões que satisfazem a verificação de segurança, todo o construtor diferente do padrão falhará, e uma exceção de segurança será gerada.  O tipo de valor não é desalocada; é deixado no conjunto do estado pelo construtor padrão.  Não suponha que um chamador que transmite uma instância do tipo de valor tem permissão para criar ou acessar a instância.  
  
## Como Corrigir Violações  
 Não é possível corrigir uma violação desta regra a menos que você remover a verificação de segurança de tipo, e usa verificações de segurança no nível de método em seu lugar.  Observe que para corrigir a violação assim não impedirá que os chamadores com permissões inadequadas obtenham instâncias do tipo de valor.  Você deve garantir que uma instância do tipo de valor, em seu estado padrão, não expõe informações confidenciais, e não pode ser usado em uma maneira prejudicial.  
  
## Quando Suprimir Alertas  
 Você pode suprimir um aviso dessa regra se qualquer chamador pode obter instâncias do tipo de valor em seu estado padrão sem gerar uma ameaça à segurança.  
  
## Exemplo  
 O exemplo a seguir mostra uma biblioteca que contém um tipo de valor que viola esta regra.  Observe que o tipo de `StructureManager` supõe que um chamador que transmite uma instância do tipo de valor tem permissão para criar ou acessar a instância.  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## Exemplo  
 O aplicativo seguir demonstra a fraqueza de biblioteca.  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **Construtor personalizado da estrutura: Falha na solicitação.**  
**Novos valores SecuredTypeStructure 100 100**  
**Novos valores SecuredTypeStructure 200 200**   
## Consulte também  
 [Demandas de link](../Topic/Link%20Demands.md)   
 [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)