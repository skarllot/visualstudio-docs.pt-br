---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Net.WebException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe WebException"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Net.WebException
Um <xref:System.Net.WebException> exceção é lançada quando ocorre um erro ao acessar a rede por meio de um protocolo conectável.  
  
## Dicas associadas  
 **Verifique a propriedade Response da exceção para determinar porque a solicitação falhou.**  
 Quando um <xref:System.Net.WebException> exceção é gerada por um descendente da <xref:System.Net.WebRequest> classe, o <xref:System.Net.WebException.Response%2A> propriedade fornece a resposta da Internet para o aplicativo.  
  
 **Verifique a propriedade Status da exceção para determinar porque a solicitação falhou.**  
 O <xref:System.Net.WebException.Status%2A> propriedade da exceção fornece informações de status para o erro. Para obter mais informações, consulte <xref:System.Net.WebExceptionStatus>.  
  
 **Se você está excedendo o tempo limite ao entrar em um serviço Web XML, defina o valor de tempo limite para a chamada de serviço Web XML como infinito.**  
 Para obter mais informações, consulte [Erro: tempo limite durante a depuração de serviços Web](../debugger/error-timeout-while-debugging-web-services.md).  
  
## Consulte também  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Como: enviar dados usando a classe WebRequest](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Como: solicitar dados usando a classe WebRequest](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Como: recuperar um WebResponse específicas de protocolo que corresponde a uma WebRequest](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)