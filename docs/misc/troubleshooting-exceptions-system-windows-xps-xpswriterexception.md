---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Windows.Xps.XpsWriterException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "Exceção System.Windows.Xps.XpsWriterException"
  - "Exceção XpsWriterException"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Windows.Xps.XpsWriterException
Um <xref:System.Windows.Xps.XpsWriterException> exceção é lançada quando um método um <xref:System.Windows.Xps.XpsDocumentWriter> ou um <xref:System.Windows.Xps.VisualsToXpsDocument> objeto chamado é incompatível com o estado atual do objeto.  
  
## Comentários  
 Por exemplo, essa exceção é lançada se o `CancelAsync` método de qualquer tipo de objeto é chamado quando o objeto não está executando uma operação de gravação assíncrona.  
  
## Consulte também  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)