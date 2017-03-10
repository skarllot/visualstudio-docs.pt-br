---
title: "Erro MSB3253 (MSBuild) | Microsoft Docs"
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
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3253 (MSBuild)
**MSB3254: O assembly \<name\> referenciado no projeto depende de \<name2\> que não está contido no perfil de cliente do .NET Framework.**  
  
 Um dos assemblies, ou de assemblies dependentes, referenciados no projeto depende de outro assembly que não está contido em [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  
  
 Esta mensagem normalmente ocorre quando um projeto referencia um controle ou uma DLL de terceiros próprio que referencia um assembly externo.  Por exemplo, um projeto usa um controle que usa por sua vez a funcionalidade que está contida em [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]completo.  Se o aplicativo novamente se destina a [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] e instalado em um sistema que não tem [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)], o aplicativo pode não funcionar corretamente se tentar acessar a funcionalidade que não está contida no subconjunto de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] .  
  
 Esta mensagem de erro “” é realmente apenas um aviso; o aplicativo continuará compilando.  No entanto, pode falhar posteriormente se o controle ou DLL a funcionalidade que está localizado em um assembly ausente.  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] é um subconjunto da biblioteca em tempo de execução completa de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3,5.  Para obter mais informações sobre o [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], consulte [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Para corrigir este erro  
  
-   Remova a referência especificada do projeto, ou direcionar [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] completo em vez de biblioteca de subconjunto de [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] .  Para obter informações sobre como definir o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] completo, consulte [Como destinar uma versão do .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Consulte também  
 [Estrutura de destino e plataforma de destino](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionais](../msbuild/additional-msbuild-resources.md)