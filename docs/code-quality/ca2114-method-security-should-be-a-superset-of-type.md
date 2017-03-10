---
title: "CA2114: a seguran&#231;a de m&#233;todo deve ser um superconjunto de tipo | Microsoft Docs"
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
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114: a seguran&#231;a de m&#233;todo deve ser um superconjunto de tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo tem a segurança declarativa e um de seus métodos tem a segurança declarativa para a mesma ação de segurança, e a ação de segurança não é [Demandas de link](../Topic/Link%20Demands.md) ou [Inheritance Demands](http://msdn.microsoft.com/pt-br/28b9adbb-8f08-4f10-b856-dbf59eb932d9), e as permissões verificadas pelo tipo não são um subconjunto das permissões verificadas pelo método.  
  
## Descrição da Regra  
 Um método não deve ter um nível de método e segurança declarativa de classificação nível para a mesma ação.  As duas verificações não são combinadas; somente a procura de nível de método é aplicada.  Por exemplo, se um tipo requer a permissão `X`, e um de seus métodos requer a permissão `Y`, código não tem que ter a permissão `X` executar o método.  
  
## Como Corrigir Violações  
 Revisar seu código para assegurar que ambas as ações são necessárias.  Se ambas as ações são necessárias, verifique se a ação de nível de método inclui a segurança especificada no nível do tipo.  Por exemplo, se seu tipo requer a permissão `X`, e seu método também deve exigir a permissão `Y`, o método deve solicitar explicitamente `X` e `Y`.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o método não requer segurança especificada pelo tipo.  No entanto, isso não é um cenário comum e pode indicar a necessidade para revisão de projeto cuidadosa.  
  
## Exemplo  
 O exemplo a seguir usa permissões de ambiente demonstrar os perigos de violar esta regra.  Neste exemplo, o código do aplicativo cria uma instância do tipo protegido antes de negar a permissão necessária do tipo.  Em um cenário de ameaça do mundo real, o aplicativo pode exigir outra maneira de fazer uma instância do objeto.  
  
 No exemplo a seguir, as demandas da biblioteca permissão de gravação para um tipo e uma permissão de leitura para um método.  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## Exemplo  
 O seguinte código do aplicativo demonstra a vulnerabilidades da biblioteca chamando o método mesmo que não satisfaz o requisito de segurança de classificação nível.  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **\[Informações pessoais de todas as permissões\]: 6\/16\/1964 de 12:00: 00 AM**  
**\[Nenhuma permissão de gravação \(necessária do tipo\)\] Informações pessoais: 6\/16\/1964 de 12:00: 00 AM**  
**\[Nenhuma permissão de leitura \(exigida pelo método\)\] Não foi possível acessar informações pessoais: A solicitação falha.**   
## Consulte também  
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/pt-br/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Demandas de link](../Topic/Link%20Demands.md)   
 [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)