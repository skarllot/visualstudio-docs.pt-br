---
title: "Nome de fonte especificado em EventLogSource est&#225; registrado em um log diferente do especificado em EventLogName | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nome de fonte especificado em EventLogSource est&#225; registrado em um log diferente do especificado em EventLogName
O `EventLog` está tentando fazer referência a uma fonte que está registrada em um log diferente. Se você está escrevendo entradas para um log de eventos, você deve especificar o <xref:System.Diagnostics.EventLog.Source%2A> propriedade. O <xref:System.Diagnostics.EventLog.Source%2A> propriedade registra seu componente com o log de eventos como uma fonte válida de entradas. Uma única fonte pode ser associado \(e, portanto, gravar entradas para\) apenas um log de eventos por vez.  
  
 Por padrão, se você tentar gravar uma entrada sem primeiro ter registrado o componente como uma fonte válida, o sistema automaticamente registra a fonte com o log de eventos, usando o valor da <xref:System.Diagnostics.EventLog.Source%2A> a propriedade como a cadeia de caracteres de origem.  
  
### Para corrigir este erro  
  
-   Verifique se que a fonte é registrada no log correto. Para fazer isso, use o <xref:System.Diagnostics.EventLog.CreateEventSource%2A> método ou uma de suas sobrecargas para especificar uma cadeia de caracteres que identifica unicamente seu componente ao log de eventos.  
  
## Consulte também  
 [Administering Event Logs](http://msdn.microsoft.com/pt-br/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [Event Log References](http://msdn.microsoft.com/pt-br/4af0661c-6c96-49f4-961d-b26ed9bc3e87)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/pt-br/948ff920-a739-4e66-a191-ee951512d42c)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/pt-br/bc66c900-4b8a-426a-b8e2-17031a20167e)