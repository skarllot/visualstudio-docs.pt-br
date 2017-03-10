---
title: "Tarefa BscMake | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.bscmake"
  - "VC.Project.VCBscMakeTool.PreserveSBR"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "Tarefa BscMake (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), tarefas"
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa BscMake
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  BSCMake não é mais usada pelo IDE do Visual Studio.  Desde o Visual Studio 2008, as informações de procura são armazenadas automaticamente em um arquivo. sdf na pasta da solução.  
  
 Encapsula a Microsoft procurar manutenção ferramenta Utilitário de informações \(bscmake.exe\).  A ferramenta bscmake.exe cria um arquivo de informações de procura \(. bsc\) navegador dos arquivos de origem \(. SBR\) que são criados durante a compilação.  Use o **Pesquisador de objetos** para exibir um arquivo. bsc.  Para obter mais informações, consulte [Referência de BSCMAKE](/visual-cpp/build/reference/bscmake-reference).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros do **BscMake** tarefa.  A maioria dos parâmetros da tarefa correspondem a uma opção de linha de comando.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**AdditionalOptions**|Parâmetro **String** opcional.<br /><br /> Uma lista de opções, conforme especificado na linha de comando.  Por exemplo, "\/*opção 1* \/*option2* \/*opção \#*".  Use esse parâmetro para especificar as opções que não são representadas por qualquer outra **BscMake** de tarefa.<br /><br /> Para obter mais informações, consulte as opções no [Opções de BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**OutputFile**|Parâmetro **String** opcional.<br /><br /> Especifica um nome de arquivo que substitui o nome do arquivo de saída padrão.<br /><br /> Para obter mais informações, consulte o **\/o** opção [Opções de BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, força uma compilação nonincremental.  Uma compilação completa, nonincremental ocorre independentemente se existe um arquivo. bsc e impede que arquivos. SBR sendo truncado.<br /><br /> Para obter mais informações, consulte o **\/n** opção [Opções de BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**Sources**|Parâmetro **ITaskItem\[\]** opcional.<br /><br /> Define uma matriz de itens de arquivo de origem do MSBuild que podem ser consumidos e emitido por tarefas.|  
|**SuppressStartupBanner**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, impede a exibição da mensagem de número de versão e copyright quando a tarefa é iniciada.<br /><br /> Para obter mais informações, consulte o **\/NOLOGO** opção [Opções de BSCMAKE](/visual-cpp/build/reference/bscmake-options).|  
|**TrackerLogDirectory**|Parâmetro **String** opcional.<br /><br /> Especifica o diretório de log do controlador.|  
  
## Comentários  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)