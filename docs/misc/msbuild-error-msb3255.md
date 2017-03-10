---
title: "Erro MSB3255 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3255"
ms.assetid: baac844e-a662-4421-bed1-2bc98f2e1cdf
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3255 (MSBuild)
**MSB3255: Não pôde localizar os arquivos de subconjunto de Framework de destino nos diretórios de Framework de destino ou em locais especificados no InstalledAssemblySubsetTables.**  
  
 Este erro ocorre quando um nome é passado para a propriedade de <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.FullTargetFrameworkSubsetNames%2A> , mas um subconjunto com esse nome não pode ser encontrado.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] é um subconjunto da biblioteca em tempo de execução completa de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3,5.  Para obter mais informações sobre o [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], consulte [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Procedimentos  
  
### Para corrigir este erro  
  
-   Coloque uma cópia do arquivo do subconjunto na pasta do framework de destino ou em um dos locais especificados em <xref:Microsoft.Build.Tasks.ResolveAssemblyReference.InstalledAssemblySubsetTables%2A>.  
  
## Consulte também  
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)