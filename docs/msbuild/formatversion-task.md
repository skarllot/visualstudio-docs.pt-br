---
title: "Tarefa FormatVersion | Microsoft Docs"
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
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa FormatVersion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Acrescenta o número de revisão para o número da versão.  
  
-   Caso n º 1: Entrada: versão \= \<undefined\> Revisão \= \< não se preocupa com \>; Saída: OutputVersion \= "1.0.0.0"  
  
-   Caso n º 2: Entrada: versão \= revisão "1.0.0.\*" \= "5" de saída: OutputVersion \= "1.0.0.5"  
  
-   Caso n º 3: Entrada: versão \= "1.0.0.0" revisão \= \< não se preocupa com \>; Saída: OutputVersion \= "1.0.0.0"  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `FormatVersion` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`FormatType`|Opcional `String` parâmetro.<br /><br /> Especifica o tipo de formato.<br /><br /> -   "Versão" \= a versão.<br />-   "Caminho"\= substituir"." com "\_";|  
|`OutputVersion`|Opcional `String` parâmetro de saída.<br /><br /> Especifica a versão de saída que inclui o número de revisão.|  
|`Revision`|Opcional `Int32` parâmetro.<br /><br /> Especifica a revisão para acrescentar à versão.|  
|`Version`|Opcional `String` parâmetro.<br /><br /> Especifica a seqüência de número de versão para formatar.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)