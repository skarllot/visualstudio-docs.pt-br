---
title: "Como solucionar problemas de atualiza&#231;&#245;es de projeto do Visual Studio malsucedidas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisualStudio.SourceControl.CannotOpenFromSourceControlDSW"
  - "vs.UpgradeProjectSolution.8.0"
helpviewer_keywords: 
  - "Atualizando aplicativos Visual Studio"
  - "atualizando projetos [Visual Studio]"
  - "projetos [Visual Studio], atualizando"
  - "Assistente de Conversão do Visual Studio"
  - "Assistente de conversão"
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 30
caps.handback.revision: 30
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Como solucionar problemas de atualiza&#231;&#245;es de projeto do Visual Studio malsucedidas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Às vezes, o Visual Studio totalmente não pode converter um projeto de uma versão anterior do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se as dicas nas seções a seguir não resolver seu problema específico, você poderá encontrar mais informações sobre o TechNet [Wiki: Portal de desenvolvimento](http://go.microsoft.com/fwlink/?LinkId=254808).  
  
## O projeto não será executado porque os arquivos não forem encontrados  
 Um arquivo de projeto contém caminhos de arquivo embutidos que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa para executar o projeto quando você pressiona F5. Esses caminhos podem incluir o local do devenv.exe e outros arquivos necessários. Em uma versão atualizada do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], os caminhos desses arquivos podem ter sido alterados.  
  
#### Para resolver caminhos de arquivo incorreto  
  
1.  Abra o arquivo de projeto em um editor de texto.  
  
2.  Verificar se há caminhos de arquivo podem estar incorretos, especialmente aquelas que contêm um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] número de versão.  
  
3.  Modificar caminhos de arquivo incorreto para que eles apontem para os novos destinos.  
  
## O projeto não será compilado porque as referências não são válidas  
 Quando você atualiza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], você também pode atualizar o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versão. Se o projeto contém referências que estão descontinuadas na mais recente [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versão, eles podem não ser resolvidas corretamente. Isso é especialmente provável para referências que incluem números de versão, por exemplo, `Microsoft.VisualStudio.Shell.Interop.8.0`.  
  
 Se seu código tiver muitas referências inválidas, a solução mais fácil seria usar o recurso de multiplataforma do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para direcionar uma versão anterior para o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Para resolver referências incorretas  
  
1.  Abra o arquivo de projeto em um editor de texto.  
  
2.  Abra as propriedades do projeto.  
  
3.  Selecione a planilha **Target Framework** valor. Como alternativa, você pode modificar o valor de `<TargetFrameworkVersion>` elemento diretamente no arquivo de projeto.  
  
 Se você deseja que seu projeto para executar no atualizados [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versão, você deve atualizar as referências do projeto e também atualizar quaisquer `Imports` ou `Using` instruções que chamam as referências. Se seu projeto for carregado no IDE, você pode atualizar as referências usando **Solution Explorer** ou **Gerenciador de referências** caixa de diálogo.  
  
## Consulte também  
 [\/Upgrade](../ide/reference/upgrade-devenv-exe.md)   
 [Converting to ASP.NET 4](../Topic/Converting%20to%20ASP.NET%204.md)