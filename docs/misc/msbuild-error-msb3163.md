---
title: "Erro MSB3163 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.InvalidComponentsLocation"
helpviewer_keywords: 
  - "MSB3163"
ms.assetid: 35c5efbf-2fd7-478c-bb8e-3c4eabb3e4d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3163 (MSBuild)
**MSB3163: O parâmetro de entrada de compilação ' ComponentsLocation \='\< ComponentsLocation \> ' não é válido. O valor deve ser 'HomeSite', 'Relative' ou 'Absolute'. O padrão é 'HomeSite'.**  
  
 Esse erro ocorre quando o valor especificado para o `ComponentsLocation` propriedade \(o local do qual os pré\-requisitos estiverem instalados\) é inválido.`ComponentsLocation` deve ser um dos três valores: `HomeSite`, `Relative`, ou `Absolute`.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)