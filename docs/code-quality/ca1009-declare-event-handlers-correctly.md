---
title: "CA1009: declarar manipuladores de eventos corretamente | Microsoft Docs"
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
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1009: declarar manipuladores de eventos corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um representante que manipula um público ou um evento protegido não tem a assinatura, o tipo de retorno, ou nomes de parâmetro corretos.  
  
## Descrição da Regra  
 Os métodos do manipulador de eventos usam dois parâmetros.  O primeiro é do tipo <xref:System.Object?displayProperty=fullName> e é denominado “remetente”.  Este é o objeto que gerou o evento.  O segundo parâmetro é do tipo <xref:System.EventArgs?displayProperty=fullName> e é denominado “e”.  Estes são os dados associados ao evento.  Por exemplo, se o evento é gerado sempre que um arquivo é aberto, os dados de evento normalmente contêm o nome do arquivo.  
  
 Os métodos do manipulador de eventos não devem retornar um valor.  Na linguagem de programação C\#, isso é indicado por tipo de retorno `void`.  Um manipulador de eventos pode chamar vários métodos em vários objetos.  Se os métodos eram permitidos retornar um valor, vários valores de retorno se para cada evento, e apenas o valor do método mais recente que foi invocado estariam disponíveis.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, corrija a assinatura, o tipo de retorno, ou nomes de parâmetro de delegação.  Para obter detalhes, consulte o exemplo.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um delegado que é indicado para tratar eventos.  Os métodos que podem ser chamadas pelo manipulador de eventos seguem à assinatura que é especificada nas diretrizes de design.  `AlarmEventHandler` é o nome do tipo delegado.  `AlarmEventArgs` é derivado da classe base de dados do evento, <xref:System.EventArgs>, e as propriedades alarmam dados do evento.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## Regras Relacionadas  
 [CA2109: revisar manipuladores de eventos visíveis](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## Consulte também  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Delegados e eventos](http://msdn.microsoft.com/pt-br/d98fd58b-fa4f-4598-8378-addf4355a115)