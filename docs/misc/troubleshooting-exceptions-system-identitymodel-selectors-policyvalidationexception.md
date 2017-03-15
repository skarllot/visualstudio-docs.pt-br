---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
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
  - "Exceção PolicyValidationException"
  - "Exceção System.IdentityModel.Selectors.PolicyValidationException"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IdentityModel.Selectors.PolicyValidationException
Um <xref:System.IdentityModel.Selectors.PolicyValidationException> exceção é lançada quando a política fornecida pelo destinatário não pode ser validada. Para obter mais informações sobre os requisitos de política, consulte [uma referência técnica para o perfil de cartão de informações v 1.0](http://go.microsoft.com/fwlink/?LinkID=102401).  
  
 Qualquer conteúdo inválido de política pode provocar essa falha. Problemas comuns com o conteúdo de política incluem o seguinte:  
  
-   Tipo de chave inválido  
  
-   Tamanho de chave inválido  
  
-   XML inválido  
  
-   Nenhuma declaração especificada na política \(pelo menos uma declaração não opcional deve ser especificada\)  
  
## Consulte também  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)