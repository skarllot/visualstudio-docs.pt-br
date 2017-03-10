---
title: "Erro MSB3188 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PrerequisiteNotSigned"
helpviewer_keywords: 
  - "MSB3188"
ms.assetid: 8520e960-3b31-4e25-9fce-b9092b869bd0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3188 (MSBuild)
**MSB3188: Assembly '\< assembly \>' deve conter uma assinatura forte para ser marcado como um pré\-requisito.**  
  
 Esse erro é gerado quando um assembly de pré\-requisito não é forte assinado. Aplica\-se somente a manifestos de aplicativo.  
  
### Para corrigir este erro  
  
-   Verifique se todos os assemblies que o projeto usa forte assinado.