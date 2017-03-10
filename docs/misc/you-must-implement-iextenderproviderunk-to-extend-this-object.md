---
title: "Implemente um IExtenderProviderUnk para estender o objeto. | Microsoft Docs"
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
  - "vs.message.VS_E_EXT_NONDISPATCHEXTENDEE"
ms.assetid: e0d4087f-9fa9-4fa9-92d9-7aed3103b2d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Implemente um IExtenderProviderUnk para estender o objeto.
O objeto estendido é baseado no IUnknown, em vez da interface IDispatch.  
  
### Para corrigir este erro  
  
1.  Ter o provedor do extensor que implemente um IExtenderProviderUnk em vez de IExtenderProvider.  
  
## Consulte também  
 <xref:EnvDTE.IExtenderProviderUnk>   
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>