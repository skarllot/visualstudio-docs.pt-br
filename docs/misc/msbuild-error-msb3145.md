---
title: "Erro MSB3145 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.InvalidUrl"
helpviewer_keywords: 
  - "MSB3145"
ms.assetid: 183d4e7e-bdc6-402f-a1b6-531505be605f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3145 (MSBuild)
**MSB3145: Parâmetro de entrada de compilação ' \< propriedade \> \= \< valor \>' não é uma url da web nem compartilhamento UNC.**  
  
 Esse erro ocorre quando o valor de `SupportUrl`, `ComponentsUrl`, ou `ApplicationUrl` propriedade do projeto não é válida. O valor deve ser um caminho URI ou UNC válido.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)