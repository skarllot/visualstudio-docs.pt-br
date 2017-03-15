---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
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
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "Exceção System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException"
  - "Exceção TrackingProfileDeserializationException"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
Um <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> exceção é lançada quando um documento XML não pode ser desserializado em um <xref:System.Workflow.Runtime.Tracking.TrackingProfile> por um <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer>.  
  
## Comentários  
 Quando o <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> lança esta exceção, ele fornece uma mensagem que descreve o motivo da exceção. Em alguns casos, o <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> fornece uma lista de erros de validação e avisos que encontrou ao tentar desserializar o <xref:System.Workflow.Runtime.Tracking.TrackingProfile>. Se essa lista for fornecida, o <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A> propriedade contém.  
  
## Consulte também  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)