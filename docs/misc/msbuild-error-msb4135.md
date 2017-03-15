---
title: "Erro MSB4135 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4135"
ms.assetid: 9192f772-ad13-42f7-b53f-c5e31846fa5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB4135 (MSBuild)
**MSB4135: Erro ao ler informações do kit de ferramentas de chave de Registro “'\<key\>'” ou uma subchave. '  \<key\>'**  
  
 Informações personalizadas do kit de ferramentas definida no Registro não pôde ser lido.  
  
### Para corrigir este erro  
  
-   Se você tiver definido um conjunto de ferramentas personalizado no Registro, certifique\-se que está no formato válido do Registro, que é tem o nome correto de `ToolsVersion` e que `MSBuildBinPath` ou o valor correto de `MSBuildToolsPath` .  
  
## Consulte também  
 [Configurações padrão e personalizadas do Toolset](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)