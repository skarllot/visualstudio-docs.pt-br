---
title: "CA1020: evitar namespaces com poucos tipos | Microsoft Docs"
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
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1020: evitar namespaces com poucos tipos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um namespace diferente do namespace global contiver menos de cinco tipos.  
  
## Descrição da Regra  
 Verifique se cada um de seus namespaces tiver uma organização lógica, e que um motivo válido existe para colocar em um namespace escassa preenchida.  Os namespaces devem conter os tipos que são usados em conjunto na maioria dos cenários.  Quando os aplicativos são mutuamente exclusivos, os tipos devem ser localizados em namespaces separadas.  Por exemplo, o namespace de <xref:System.Web.UI> contém tipos que são usados em aplicativos Web, e o namespace de <xref:System.Windows.Forms> contém tipos que são usados em aplicativos baseados no de [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)].  Mesmo que as duas namespaces tem tipos que controlam aspectos da interface do usuário, esses tipos não são projetados para uso no mesmo aplicativo.  Consequentemente, estão localizados em namespaces separadas.  A organização cuidadosa de namespace também pode ser útil porque aumenta a capacidade de descoberta de um recurso.  Revisando a hierarquia de namespace da biblioteca, os consumidores devem conseguir localizar os tipos que implementam um recurso.  
  
> [!NOTE]
>  Os tipos de tempo de design e as permissões não devem ser mesclados em outros namespaces de acordo com essa diretriz.  Esses tipos pertencem em seus próprios namespaces abaixo de seu namespace principal, e namespaces devem terminar em `.Design` e em `.Permissions`, respectivamente.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, tente combinar os namespaces que contêm apenas alguns tipos em um único namespace.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra não quando o namespace contém tipos que são usados com os tipos em suas outros namespaces.