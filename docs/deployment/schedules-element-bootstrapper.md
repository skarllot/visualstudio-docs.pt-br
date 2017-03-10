---
title: "Elemento &lt;Schedules&gt; (bootstrapper) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Elemento <Schedules> [bootstrapper]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Elemento &lt;Schedules&gt; (bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O `Schedules` elemento contém `Schedule` elementos, que definem os horários específicos em quais comandos definidos pela `Command` elemento deve ser executado.  
  
## Sintaxe  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## Elementos e atributos  
 O `Schedules` elemento é filho de `Product` elemento.  Cada `Product` elemento pode ter no máximo uma `Schedules` elemento.  O `Schedules` elemento não tem nenhum atributo.  
  
## Agenda  
 O `Schedule` elemento é filho de `Schedules` elemento.  A `Schedules` elemento deve ter pelo menos um `Schedule` elemento.  
  
 `Schedule`tem o atributo a seguir.  
  
|Atributo|Descrição|  
|--------------|---------------|  
|`Name`|Obrigatório.  O nome do item de agenda.  Isso corresponde do `ScheduleName` propriedade da `Command` elemento.  Quando um `Command` faz referência a agenda nomeada, ela só será executada no momento indicado pelo que `Schedule` elemento.  Agendas também podem ser associadas a `FailIf` e `BypassIf` elementos, que restringem a esses testes condicionais para execução no agendamento especificado.  Para obter mais informações, consulte [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
  
 Um dado `Schedule` elemento pode ter exatamente um dos seguintes filhos.  
  
## BuildList  
 O `BuildList` elemento instrui o instalador para executar um comando imediatamente depois que o aplicativo de inicialização é iniciado.  
  
## BeforePackage  
 O `BeforePackage` elemento instrui o instalador para executar um comando antes que o pacote especificado está instalado.  
  
## AfterPackage  
 O `AfterPackage` elemento instrui o instalador para executar um comando após a instalação do pacote especificado.  
  
## Consulte também  
 [Elemento \<Product\>](../deployment/product-element-bootstrapper.md)   
 [Referência de esquema de produto e pacote](../deployment/product-and-package-schema-reference.md)