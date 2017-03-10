---
title: "Tarefa CPPClean | Microsoft Docs"
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
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "tarefa CPPClean (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), tarefa CPPClean"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa CPPClean
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Exclui os arquivos temporários que MSBuild cria quando um projeto do Visual C\+\+ é construído.  O processo de exclusão de arquivos de compilação é conhecido como  *de limpeza*.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da **CPPClean** tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|**DeletedFiles**|Opcional `ITaskItem[]` parâmetro de saída.<br /><br /> Define uma matriz de itens de arquivo de saída MSBuild que pode ser consumido e emitido por tarefas.|  
|**DoDelete**|Opcional **Boolean** parâmetro.<br /><br /> Se `true`, limpa temporary criar arquivos.|  
|**FilePatternsToDeleteOnClean**|Obrigatório `String` parâmetro.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de extensões de arquivo dos arquivos para limpar.|  
|**FilesExcludedFromClean**|Opcional `String` parâmetro.<br /><br /> Especifica uma lista delimitada por ponto e de arquivos não para limpar.|  
|**FoldersToClean**|Obrigatório `String` parâmetro.<br /><br /> Especifica uma lista delimitada por ponto e de diretórios para limpar.  Você pode especificar um completo ou um caminho relativo e o caminho pode conter o símbolo curinga \(**\***\).|  
  
## Comentários  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)