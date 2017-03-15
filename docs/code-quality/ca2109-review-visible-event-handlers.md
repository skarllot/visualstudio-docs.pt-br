---
title: "CA2109: revisar manipuladores de eventos vis&#237;veis | Microsoft Docs"
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
  - "CA2109"
  - "ReviewVisibleEventHandlers"
helpviewer_keywords: 
  - "CA2109"
  - "ReviewVisibleEventHandlers"
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2109: revisar manipuladores de eventos vis&#237;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewVisibleEventHandlers|  
|CheckId|CA2109|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um método protegido de manipulação de eventos foram detectados.  
  
## Descrição da Regra  
 Um método externamente visível de manipulação de eventos apresenta um problema de segurança que requer análise.  
  
 Os métodos de manipulação de eventos não são expostos a menos que seja absolutamente necessário.  Um manipulador de eventos, um tipo delegado, que chama o método expõe pode ser adicionado a qualquer evento enquanto assinaturas e do manipulador de eventos correspondem.  Os eventos podem potencialmente serem gerados por todo o código, e são gerados frequentemente pelo código do sistema altamente confiáveis em resposta a ações do usuário como clique em um botão.  Adicionar uma verificação de segurança a um método de manipulação de eventos não impede que o código registra um manipulador de eventos que chama o método.  
  
 Procura uma forma confiável não pode proteger um método chamado por um manipulador de eventos.  Exigências de segurança ajudam a proteger o código dos chamadores não confiáveis revisando os chamadores na pilha de chamadas.  O código que adicionar um manipulador de eventos a um evento não está necessariamente atual da pilha de chamadas quando os métodos do manipulador de eventos.  Consequentemente, a pilha de chamadas pode ter apenas altamente confiável chamadores quando o método do manipulador de eventos é invocado.  Isso faz com que as demandas feitas pelo método do manipulador de eventos para ter êxito.  Além disso, a permissão necessária pode ser declarada quando o método é invocado.  Pelos motivos a seguir, o risco de não corrigir uma violação desta regra só pode ser avaliado depois de revisar o método de manipulação de eventos.  Ao revisar seu código, considere os seguintes problemas:  
  
-   O manipulador de eventos executar qualquer operação que é perigosa ou explorável, como declarar permissões ou suprimir a permissão de código não gerenciado?  
  
-   Quais são as ameaças de segurança para e do código porque podem executar a qualquer momento com apenas os chamadores altamente confiáveis na pilha?  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, revise o método e avaliar o seguinte:  
  
-   Você pode fazer o não utilitário do método de manipulação de eventos?  
  
-   Você pode mover toda a funcionalidade perigosa fora do manipulador de eventos?  
  
-   Se uma procura de segurança é imposta, essa pode ser realizado em alguma outra forma?  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra somente depois revisão de segurança cuidadosa garantir que seu código não gerencie uma ameaça à segurança.  
  
## Exemplo  
 O código a seguir mostra um método de manipulação de eventos que pode ser implantada criados pelo código mal\-intencionado.  
  
 [!code-cs[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]  
  
## Consulte também  
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>   
 <xref:System.EventArgs?displayProperty=fullName>   
 [Security Demands](http://msdn.microsoft.com/pt-br/324c14f8-54ff-494d-9fd1-bfd20962c8ba)