---
title: "Caixa de di&#225;logo Estrutura de Destino do Projeto N&#227;o Instalada | Microsoft Docs"
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
  - "vs.TargetFrameworkNotFound"
ms.assetid: 64ce8743-d5bd-447e-ba10-54b2aafe109e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Caixa de di&#225;logo Estrutura de Destino do Projeto N&#227;o Instalada
Você abriu um projeto que tem como alvo uma estrutura que não está instalada no seu computador. Para continuar, você deve selecionar uma das opções na caixa de diálogo.  
  
> [!NOTE]
>  Sempre que você baixar e instalar uma nova estrutura, você deve reiniciar o Visual Studio.  
  
## Visual Basic e Visual C\#  
 Se você abrir um projeto Visual Basic ou Visual c\#, selecione uma das opções a seguir.  
  
 **Altere o destino para o .NET Framework 4.5. Você pode alterar para o .NET Framework** *versão*  **em um momento posterior.**  
 Retargets seu projeto para o .NET Framework 4.5. Você pode posteriormente reinstalar a versão anterior e, em seguida, redirecionar o projeto.  
  
 **Baixe o pacote de direcionamento do .NET Framework \< versão \>. O projeto não será alterado.**  
 Abre o site Microsoft Download Center, onde você pode baixar a versão do .NET Framework que você deseja. O projeto é descarregado da solução. Depois de baixar e instalar o framework desejado, você deve reiniciar o Visual Studio e reabra o projeto.  
  
 **Não carregar o projeto.**  
 Deixa o projeto descarregado da solução. Você pode instalar posteriormente o Framework desejado e, em seguida, recarregue o projeto.  
  
## Visual C\+\+  
 Se você abrir um projeto do Visual C\+\+, selecione uma das opções a seguir.  
  
 **Baixar o pacote de direcionamento do .NET Framework** *versão***. O projeto não será alterado.**  
 Abre o site Microsoft Download Center, onde você pode baixar a versão do .NET Framework que você deseja. Depois que o download for concluído, o projeto é redirecionado para essa versão. O projeto é descarregado da solução. Depois de baixar e instalar o framework desejado, você deve reiniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], e, em seguida, reabra o projeto.  
  
 **Não carregar o projeto.**  
 Deixa o projeto descarregado da solução. Você pode instalar posteriormente o Framework desejado e, em seguida, recarregue o projeto.  
  
## Consulte também  
 [Como destinar uma versão do .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Solução de problemas com erros de direcionamento do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Adicionando referências](/visual-cpp/ide/adding-references-in-visual-cpp-projects)