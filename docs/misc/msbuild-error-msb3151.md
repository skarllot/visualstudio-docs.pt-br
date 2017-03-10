---
title: "Erro MSB3151 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
helpviewer_keywords: 
  - "MSB3151"
ms.assetid: e4766734-2e90-436e-850b-a8a9da535dee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3151 (MSBuild)
**MSB3151: Item '\< pacote \>' já inclui '\< pacote \>'.**  
  
 Este aviso ocorre quando você tiver selecionado dois pacotes de bootstrapper e um pacote está incluído no outro \(por exemplo, selecionando o pacote incluído é redundante\).  
  
### Para corrigir este erro  
  
-   Desmarque a caixa de seleção para o pacote de redundância incluído.