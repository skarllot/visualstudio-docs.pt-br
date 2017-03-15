---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Net.HttpListenerException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe HttpListenerException"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Net.HttpListenerException
Um <xref:System.Net.HttpListenerException> é lançada quando ocorre um erro processando uma solicitação do protocolo HTTP.  
  
## Dicas associadas  
 Verifique se que você não está tentando registrar um prefixo URI que já está registrado.  
 Se o prefixo URI já está registrado, essa exceção ocorrerá.  
  
 Verifique se que a solicitação HTTP é válida.  
 Essa exceção é lançada a <xref:System.Net.HttpListener> classe e suas classes associadas quando ocorre um erro durante a inicialização do <xref:System.Net.HttpListener> ou ao criar ou enviar uma resposta a uma solicitação HTTP.  
  
 Se você estiver usando o `HttpListenerPrefixCollection.Add` método, verifique se o `uriPrefix` já não tenha sido adicionado.  
 Essa exceção será lançada se outro <xref:System.Net.HttpListener> já tiver adicionado o prefixo `uriPrefix`.  
  
## Consulte também  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)