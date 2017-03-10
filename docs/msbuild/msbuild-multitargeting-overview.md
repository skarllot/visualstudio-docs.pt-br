---
title: "Vis&#227;o geral da multiplataforma no MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vis&#227;o geral da multiplataforma no MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Usando MSBuild, você pode compilar um aplicativo executar em qualquer uma das várias versões do .NET Framework, e em qualquer uma das várias plataformas do sistema.  Por exemplo, você pode compilar um aplicativo execute no.NET Framework 2.0 em uma plataforma de 32 bits, e compila o mesmo aplicativo executar no .NET Framework 4.5 em uma plataforma de 64 bits.  
  
> [!IMPORTANT]
>  Independentemente de nome “que multitargeting”, um projeto pode selecionar somente uma estrutura e somente uma plataforma de cada vez.  
  
 Estes são alguns dos recursos de definição do MSBuild:  
  
-   Você pode desenvolver um aplicativo que tem como alvo uma versão anterior do.NET Framework, por exemplo, para versões 2,0, 3,5, ou 4.  
  
-   Você pode direcionar uma estrutura diferente do.NET Framework, por exemplo, o Silverlight Framework.  
  
-   Você pode direcionar *um perfil de estrutura*, que é um subconjunto predefinido de uma estrutura de destino.  
  
-   Se um serviço de empacotamento para a versão atual do.NET Framework é solto, você pode destinar\-lo.  
  
-   MSBuild que direciona garantias que um aplicativo usa apenas funcionalidade que está disponível na estrutura e na plataforma de destino.  
  
## Destino Framework e plataforma  
 *Uma estrutura de destino* é a versão do.NET Framework que um projeto é criado executado, e *uma plataforma de destino* é a plataforma do sistema em que o projeto é compilado executar.  Por exemplo, você pode desejar utilizar um aplicativo.NET Framework 2.0 executar em uma plataforma de 32 bits que é compatível com a família do processador 802x86 \(x\).  A combinação de plataforma do framework de destino e de destino é conhecida como *o contexto de destino*.  Para obter mais informações, consulte [Estrutura de destino e plataforma de destino](../msbuild/msbuild-target-framework-and-target-platform.md).  
  
## Conjunto de Ferramentas \(ToolsVersion\)  
 Conjunto de Ferramentas coleção juntos ferramentas, as tarefas, e destinos que são usados para criar o aplicativo.  Conjunto de Ferramentas inclui compiladores como csc.exe e vbc.exe, o arquivo de destino microsoft.common.targets comum \(\), e tarefas comuns arquivo \(microsoft.common.tasks\).  4,5 Conjunto De Ferramentas podem ser usados para direcionar as versões 2,0, 3,0, 3,5, 4, e 4,5 do.NET Framework. No entanto, 2,0 Conjunto De Ferramentas podem ser usados somente para utilizar a versão 2,0 do .NET Framework.  Para obter mais informações, consulte [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## Assemblies de referência  
 Assemblies de referência que são especificados na ajuda de Conjunto De Ferramentas você criar e compilar um aplicativo.  Esses referenciam assemblies não apenas para ativar uma compilação específica de destino, mas também restringe componentes e recursos no Visual Studio IDE aquelas que são compatíveis com o destino.  Para obter mais informações, consulte [Resolvendo assemblies em tempo de design](../msbuild/resolving-assemblies-at-design-time.md)  
  
## Configurando destinos e tarefas  
 Você pode configurar destinos e executar tarefas do MSBuild para fora de processo com MSBuild de modo que você pode direcionar os contextos que são consideravelmente diferentes de aquele que você está sendo executado.  Por exemplo, você pode direcionar um de 32 bits, aplicativos.NET Framework 2.0 quando o computador de desenvolvimento executar em uma plataforma de 64 bits com o.NET Framework 4.5. Para obter mais informações, consulte [Configurando destinos e tarefas](../msbuild/configuring-targets-and-tasks.md).  
  
## Solução de problemas  
 Você pode encontrar erros se você tentar fazer referência a um assembly que não é parte do contexto de destino.  Para obter mais informações sobre esses erros e o que fazer sobre ele, consulte a [Solução de problemas com erros de direcionamento do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).