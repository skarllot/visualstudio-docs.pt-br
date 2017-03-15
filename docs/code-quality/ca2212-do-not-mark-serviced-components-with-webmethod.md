---
title: "CA2212: n&#227;o marcar componentes atendidos com WebMethod | Microsoft Docs"
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
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2212: n&#227;o marcar componentes atendidos com WebMethod
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|CheckId|CA2212|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método em um tipo que herde de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> é marcado com <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.  
  
## Descrição da Regra  
 <xref:System.Web.Services.WebMethodAttribute> se aplica aos métodos de um serviço Web XML que foram criados no ASP.NET; faz o método acessível do cliente web remotos.  O método e a classe devem ser públicos e executado em um aplicativo Web ASP.NET.  os tipos de<xref:System.EnterpriseServices.ServicedComponent> são hospedados por aplicativos COM\+ e podem usar os serviços COM\+.  <xref:System.Web.Services.WebMethodAttribute> não é aplicado aos tipos de <xref:System.EnterpriseServices.ServicedComponent> porque não devem ser usados pelos mesmos cenários.  Especificamente, adicione o atributo ao método de <xref:System.EnterpriseServices.ServicedComponent> não faz o método acessível do cliente web remotos.  Como <xref:System.Web.Services.WebMethodAttribute> e um método de <xref:System.EnterpriseServices.ServicedComponent> têm conflitantes comportamentos e os requisitos para o contexto e a transação fluem, o comportamento do método estarão incorretas em alguns cenários.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o atributo do método de <xref:System.EnterpriseServices.ServicedComponent> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Não há nenhum cenário onde combinar esses elementos está correta.  
  
## Consulte também  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>