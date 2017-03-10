---
title: "Arquivos de resposta do MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "Arquivos .rsp"
  - "MSBuild, Arquivos .rsp"
  - "MSBuild, arquivos de resposta"
  - "arquivos de resposta, MSBuild"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Arquivos de resposta do MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Arquivos de resposta \(.rsp\) são arquivos de texto que contêm as opções de linha de comando do MSBuild. exe.  Cada switch pode estar em uma linha separada ou todos os switches podem estar em uma linha.  As linhas de comentários são precedidas por um **\#** símbolo.  O **@** opção é usada para passar a outro arquivo de resposta para MSBuild. exe.  
  
 O arquivo de resposta automática é um arquivo de .rsp especial que MSBuild. exe usa automaticamente quando estiver criando um projeto.  Esse arquivo, o MSBuild, deve estar no mesmo diretório do MSBuild. exe, caso contrário, ele não será localizado.  Você pode editar esse arquivo para especificar opções de linha de comando padrão para MSBuild. exe.  Por exemplo, se você usar o agente de log mesmo sempre que você criar um projeto, você pode adicionar o **\/logger** alterne para MSBuild e MSBuild. exe usará o agente de log toda vez que um projeto é construído.  
  
## Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)