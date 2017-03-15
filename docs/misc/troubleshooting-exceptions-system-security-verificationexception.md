---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Security.VerificationException | Microsoft Docs"
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
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe VerificationException"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Security.VerificationException
Um <xref:System.Security.VerificationException> exceção é lançada quando o código seja fortemente tipado requer que a política de segurança e o processo de verificação é capaz de verificar que o código é fortemente tipado.  
  
## Dicas associadas  
 Verifique se que seu aplicativo não está carregando duas versões conflitantes de uma biblioteca de classes.  
 Como parte do processo de verificação, MSIL \(Microsoft intermediate language\) é verificado para segurança de tipo garantir que os objetos estejam isolados com segurança entre si e, portanto, estão protegidos contra corrupção acidental ou mal\-intencionada. Para obter mais informações, consulte [segurança de tipos e segurança](http://msdn.microsoft.com/pt-br/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc).  
  
## Consulte também  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)