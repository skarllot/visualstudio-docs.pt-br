---
title: "Erro MSB3113 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.ResolveFailedInReadWriteMode"
helpviewer_keywords: 
  - "MSB3113"
ms.assetid: 81e73738-e6ee-4651-9f48-acb1feef3ff5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3113 (MSBuild)
**MSB3113: Não foi possível localizar o arquivo '\< arquivo \>'.**  
  
 Esse erro é gerado quando uma referência pode resolver é encontrada durante a criação de um novo manifesto. Ele pode ter sido originadas do arquivo de projeto ou como um parâmetro de tarefa.  
  
### Para corrigir este erro  
  
-   Verifique o arquivo de projeto \(e criar parâmetros, se você estiver personalizado criando\) por conflitos em referências de arquivo.  
  
## Consulte também  
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)