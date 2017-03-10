---
title: "O provedor de extensor n&#227;o d&#225; suporte &#224;s interfaces IExtenderProvider ou IExtenderProviderUnk. | Microsoft Docs"
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
  - "vs.message.VS_E_EXT_EXTPROVINVALID"
ms.assetid: 77d596cd-28db-4ad5-bd4d-e451276e869c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O provedor de extensor n&#227;o d&#225; suporte &#224;s interfaces IExtenderProvider ou IExtenderProviderUnk.
O provedor do extensor em uso não suporta a interface implementada por você.  
  
### Para corrigir este erro  
  
1.  Implemente IExtenderProvider se o objeto estendido dá suporte à interface de automação de IDispatch.  
  
     – ou –  
  
     Implemente um IExtenderProviderUnk se o objeto estendido é baseado no IUnknown.  
  
## Consulte também  
 <xref:EnvDTE.IExtenderProviderUnk>   
 <xref:EnvDTE.IExtenderProvider>   
 <xref:EnvDTE.ObjectExtenders>