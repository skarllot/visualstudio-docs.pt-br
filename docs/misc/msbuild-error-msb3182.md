---
title: "Erro MSB3182 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.TargetPathTooLong"
helpviewer_keywords: 
  - "MSB3182"
ms.assetid: b257a206-b12b-453b-97d8-2cb9a0d3dcc9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3182 (MSBuild)
**MSB3182: Nome de arquivo '\< arquivo \>' excede os caracteres '\< length \>'.**  
  
 Esse aviso é gerado quando o valor de `TargetPath` propriedade é muito longa. Ele pode aplicar para o manifesto de aplicativo e implantação.  
  
### Para corrigir este erro  
  
-   Editar o valor da `TargetPath` propriedade para torná\-lo mais curto.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)