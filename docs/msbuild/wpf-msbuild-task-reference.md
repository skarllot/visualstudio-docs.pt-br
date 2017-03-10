---
title: "Refer&#234;ncia das tarefas do WPF MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "tarefas de compilação [WPF MSBuild], mecanismo de compilação da Microsoft"
  - "tarefas de compilação que usam o mecanismo de compilação da Microsoft [WPF MSBuild], marcação de compilação e recursos de processo"
  - "referência à tarefa WPF MSBuild [WPF MSBuild]"
  - "referência à tarefa WPF MSBuild [WPF MSBuild], tabela de termos/definições"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Refer&#234;ncia das tarefas do WPF MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O processo de compilação de Windows Presentation Foundation \(WPF\) estende o Microsoft build engine \(MSBuild\) com um conjunto adicional de tarefas de compilação, incluindo as tarefas de recursos de marcação e o processo de compilação.  
  
## Nesta seção  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Classifica um conjunto de recursos de origem como aquelas que será incorporado em um assembly.  Se um recurso não é localizável, ele é incorporado no assembly principal do aplicativo; Caso contrário, ele é incorporado a um assembly satélite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Gera um assembly, se pelo menos um [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] página em um projeto referencia um tipo que seja declarado localmente nesse projeto.  O assembly gerado é removido após a conclusão do processo de compilação ou se o processo de compilação falhar.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Retorna o diretório do atual [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] em tempo de execução.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Converte não localizáveis [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] arquivos em formato binário compilado do projeto.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Executa a compilação da marcação de segundo passo em [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] arquivos que fazem referência a tipos no mesmo projeto.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Mescla os atributos de localização e comentários de uma ou mais [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos de formato binário em um único arquivo para o assembly inteiro.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Incorpora um ou mais recursos \(. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] em formato binário e outros tipos de extensão\) em um arquivo. Resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Verifica, atualiza ou remove os identificadores exclusivos \(UIDs\), para localizar todos os [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] elementos que estão incluídos na fonte de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] arquivos.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Adiciona o  **\<hostInBrowser\/\>** elemento para o manifesto do aplicativo \(*projectname*. exe. manifest\) quando um [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] projeto é construído.  
  
## Consulte também  
 [MSBuild](http://msdn.microsoft.com/pt-br/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)