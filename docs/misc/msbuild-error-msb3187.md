---
title: "Erro MSB3187 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3187 (MSBuild)
**MSB3187: O assembly referenciado '\< assembly \>' destinado a um processador diferente do aplicativo.**  
  
 Esse aviso é gerado quando a plataforma de destino do aplicativo \(arquitetura do processador\) é definida como neutro \(MSIL\) e o assembly referenciado não é neutro ou se a arquitetura do aplicativo não é independente e a dependência é neutro. Além disso, se não forem ambos de plataforma neutra, sua arquitetura deve corresponder. Além disso, a arquitetura de aplicativos e arquitetura de assembly do ponto de entrada sempre devem corresponder.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que a plataforma de destino do aplicativo \(arquitetura do processador\) corresponde todos os assemblies referenciados e a arquitetura de conjunto de ponto de entrada.  
  
## Consulte também  
 [Caixa de diálogo Configurações de Compilador Avançadas \(Visual Basic\)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)   
 [Página de Compilação, Designer de Projeto \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)