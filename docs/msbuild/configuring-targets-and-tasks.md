---
title: "Configurando destinos e tarefas | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configurando destinos e tarefas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode configurar destinos do MSBuild e tarefas executar o para fora de processo com MSBuild de modo que você pode direcionar os contextos que diferem de que você está sendo executado.  Por exemplo, você pode direcionar um aplicativo de 32 bits do .NET Framework 2.0 quando o computador de desenvolvimento executar em um sistema operacional de 64 bits do .NET Framework 4.5.  Você também pode computadores de destino que executam com o.NET Framework 4 ou anterior.  A combinação de 32 \- ou o bitness 64 e a versão do .NET Framework específico são conhecidos como *o contexto de destino*.  
  
## Instalação  
 O.NET Framework 4.5 e os 4.5.1 substituem Common Language Runtime \(CLR\), destinos, tarefas e ferramentas, do .NET Framework 4 sem renomeá\-los.  O .NET Framework 4.5.1 é instalado como parte [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
 Se você deseja instalar MSBuild separada do Visual Studio, você pode baixar o pacote de instalação de [Download do MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745).  Você também deve instalar as versões do .NET Framework deseja usar também.  
  
## Destinos e tarefas  
 MSBuild executa determinadas tarefas de compilação fora de processo direcionar um conjunto maior de contextos.  Por exemplo, MSBuild de 32 bits pode executar uma tarefa de compilação em um processo de 64 bits para um computador de 64 bits.  Isso é controlado argumentos de `UsingTask` e por parâmetros de `Task` .  Destinos instalados pelo .NET Framework 4.5 definem esses argumentos e parâmetros, e nenhuma alteração é necessária para construir aplicativos para vários contextos de destino.  
  
 Se você desejar criar seu próprio contexto de destino, você deve definir esses argumentos e parâmetros apropriadamente.  Procure no arquivo do .NET Framework 4.5 e Microsoft.Common.targets no arquivo de Microsoft.Common.Tasks para exemplos.  Para obter informações sobre como criar uma tarefa personalizada que pode trabalhar com vários contextos de destino, ou como alterar tarefas existentes, consulte [Como configurar destinos e tarefas](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## Consulte também  
 [Multiplataforma](../msbuild/msbuild-multitargeting-overview.md)