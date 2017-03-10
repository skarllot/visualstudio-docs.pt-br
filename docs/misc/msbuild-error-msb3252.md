---
title: "Erro MSB3252 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB3252"
helpviewer_keywords: 
  - "MSB3252"
ms.assetid: 4e6982b8-84b3-4d21-94e1-05cc10bf1393
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3252 (MSBuild)
**MSB3252: O projeto possui uma referência ao assembly \<name\>.  Este assembly não é parte do perfil de cliente do .NET Framework.  Não ter essa referência pode haver compila ou erros de tempo de execução.**  
  
 Um chamada foi feita para um membro em um assembly, ou assembly dependente, que não é parte de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  Portanto, a chamada não pode ser resolvido e o aplicativo não pode ser compilado.  
  
 Para obter mais informações sobre o [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], consulte [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Para corrigir este erro  
  
-   Remova a referência especificada do assembly do seu projeto, ou direcionar [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] completo em vez de biblioteca de subconjunto de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] .  Para obter informações sobre como definir o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] completo, consulte [Como destinar uma versão do .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Consulte também  
 [Estrutura de destino e plataforma de destino](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)