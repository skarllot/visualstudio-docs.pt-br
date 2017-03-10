---
title: "Classe TaskExtension (base) | Microsoft Docs"
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
  - "MSBuild, classe base da tarefa da ferramenta"
  - "classe base da tarefa da ferramenta [MSBuild]"
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Classe TaskExtension (base)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Muitas tarefas herdam o <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Esta cadeia de herança adiciona vários parâmetros para as tarefas que derivam delas.  Esses parâmetros são listados neste documento.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros das classes base.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Opcional <xref:Microsoft.Build.Framework.IBuildEngine> parâmetro.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas.  O mecanismo de compilação automaticamente define este parâmetro para permitir que tarefas de retorno de chamada para ela.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Opcional <xref:Microsoft.Build.Framework.IBuildEngine2> parâmetro.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas.  O mecanismo de compilação automaticamente define este parâmetro para permitir que tarefas de retorno de chamada para ela.<br /><br /> Esta é uma propriedade de conveniência para que os autores de tarefa herdam essa classe não é necessário converter o valor de `IBuildEngine` para `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Opcional <xref:Microsoft.Build.Framework.IBuildEngine3> parâmetro.<br /><br /> Especifica a interface do mecanismo de compilação fornecida pelo host.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Opcional <xref:Microsoft.Build.Framework.ITaskHost> parâmetro.<br /><br /> Especifica a instância do objeto de host \(pode ser nulo\).  O mecanismo de compilação define essa propriedade se o host IDE tiver associado um objeto de host com essa tarefa específica.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Opcional <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parâmetro somente leitura.<br /><br /> Obtém um `TaskLoggingHelperExtension` objeto que contém os métodos de log da tarefa.|  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)