---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Printing.PrintingCanceledException | Microsoft Docs"
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
  - "Exceção PrintingCanceledException"
  - "Exceção System.Printing.PrintingCanceledException"
ms.assetid: bec418d6-f168-4a73-962f-5ee0427600b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Printing.PrintingCanceledException
Um <xref:System.Printing.PrintingCanceledException> exceção ocorre quando o código tenta acessar um trabalho de impressão cancelado.  
  
## Comentários  
 Se você estiver criando um aplicativo Windows Presentation Foundation \(WPF\) que inclui a funcionalidade de impressão e permite que os trabalhos de impressão a ser cancelado, certifique\-se de que trate corretamente essa exceção. Uma exceção sem tratamento desse tipo pode causar um aplicativo Windows Presentation Foundation parar de responder.  
  
## Consulte também  
 <xref:System.Printing.PrintingCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)