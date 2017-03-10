---
title: "CA2122: n&#227;o expor indiretamente m&#233;todos com demandas de link | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122: n&#227;o expor indiretamente m&#233;todos com demandas de link
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um público ou um membro protegido têm [Demandas de link](../Topic/Link%20Demands.md) e são chamados por um membro que não executa nenhum verificações de segurança.  
  
## Descrição da Regra  
 Uma procura de link verifica as permissões do chamador imediatamente somente.  Se um membro `X` não faz nenhuma procura de segurança dos chamadores, e de código de chamadas protegido por uma procura de link, um chamador sem a permissão necessária pode usar `X` para acessar o membro protegido.  
  
## Como Corrigir Violações  
 Adicionar uma segurança [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) ou vincular a procurar um membro de modo que ela não fornece acesso inseguro para o membro procura\- link protegido.  
  
## Quando Suprimir Alertas  
 Para suprimir com segurança um aviso desta regra, você deve garantir que seu código não concede aos chamadores acesso a operações ou para recursos que podem ser usados em uma forma destrutiva.  
  
## Exemplo  
 Os exemplos a seguir mostram uma biblioteca que viola a regra e, um aplicativo que demonstra a fraqueza de biblioteca.  A biblioteca de exemplo fornece dois métodos que violam junto a regra.  O método de `EnvironmentSetting` é protegida por uma procura de link para acesso irrestrito a variáveis de ambiente.  O método de `DomainInformation` não faz nenhuma procura de segurança dos chamadores antes de chamar `EnvironmentSetting`.  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## Exemplo  
 O seguinte aplicativo chama o membro de biblioteca desprotegido.  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **Valor do membro desprotegido: seattle.corp.contoso.com**   
## Consulte também  
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)   
 [Demandas de link](../Topic/Link%20Demands.md)   
 [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)