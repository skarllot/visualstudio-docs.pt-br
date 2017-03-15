---
title: "Erro MSB3184 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.InvalidInputManifest"
helpviewer_keywords: 
  - "MSB3184"
ms.assetid: 2be9f8e9-04ee-4299-b79f-965ee57a1a34
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3184 (MSBuild)
**MSB3184: Manifesto de entrada é inválido.**  
  
 Esse erro é gerado quando o processo de compilação tenta carregar um arquivo, esperando que ele contém um manifesto de aplicativo ou um manifesto de implantação, mas acontece para conter algo \(como uma data diferente de manifesto ou corrompido\).  
  
### Para corrigir este erro  
  
-   Verificar se os manifestos em seu projeto são válidos e adequados.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)