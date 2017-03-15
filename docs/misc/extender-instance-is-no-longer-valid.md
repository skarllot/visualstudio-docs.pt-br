---
title: "Inst&#226;ncia do extensor n&#227;o &#233; mais v&#225;lida. | Microsoft Docs"
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
  - "vs.message.VS_E_EXT_EXTINVALID"
ms.assetid: 6361ba35-f2c5-4024-9362-46d7d9daf651
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Inst&#226;ncia do extensor n&#227;o &#233; mais v&#225;lida.
A instância do extensor não pôde ser criada com êxito ou destruída.  
  
### Para corrigir este erro  
  
1.  Obter a instância do extensor novamente do objeto estendido  
  
     – ou –  
  
     Obtém a instância do extensor novamente chamando DTE. ObjectExtenders.GetExtender\(\).  
  
## Consulte também  
 <xref:EnvDTE.ObjectExtenders>   
 <xref:EnvDTE.ObjectExtenders.GetExtender%2A>