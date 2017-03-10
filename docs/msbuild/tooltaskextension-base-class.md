---
title: "Classe ToolTaskExtension (base) | Microsoft Docs"
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
  - "MSBuild.ToolTask.ToolCommandFailed"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Classe ToolTaskExtension (base)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Muitas tarefas herdam o <xref:Microsoft.Build.Tasks.ToolTaskExtension> classe, que herda do <xref:Microsoft.Build.Utilities.ToolTask> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Esta cadeia de herança adiciona vários parâmetros para as tarefas que derivam deles.  Esses parâmetros são listados neste documento.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros das classes base.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas.  O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas de retorno de chamada para ela.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas.  O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas de retorno de chamada para ela.<br /><br /> Esta é uma propriedade de conveniência para que os autores de tarefa herdar desta classe não é necessário converter o valor de `IBuildEngine` para `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica a interface do mecanismo de compilação fornecida pelo host.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A>|Parâmetro `bool` opcional.<br /><br /> Quando definido como `true`, essa tarefa passa **\/Q** para o cmd.exe linha de comando que a linha de comando não é copiada para stdout.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>|Opcional `String` parâmetro de matriz.<br /><br /> Matriz de pares de variáveis de ambiente, separadas por sinais de igual.  Essas variáveis são passados para o executável gerado além, ou seletivamente substituição, o bloco de ambiente regular.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A>|Opcional `Int32` somente leitura parâmetro de saída.<br /><br /> Especifica o código de saída é fornecido pelo comando executado.  Se a tarefa conectado todos os erros, mas o processo tinha um código de saída 0 \(êxito\), isso é definido como \-1.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parâmetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica a instância do objeto de host \(pode ser nulo\).  O mecanismo de compilação define essa propriedade se o IDE do host está associada a um objeto de host com essa tarefa em particular.|  
|<xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A>|Opcional <xref:Microsoft.Build.Utilities.TaskLoggingHelper> parâmetro somente leitura.<br /><br /> Obtém uma instância de um <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> classe que contém métodos de registro de tarefa.|  
|<xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A>|Opção `bool` parâmetro.<br /><br /> Se `true`, todas as mensagens recebidas no fluxo de erro padrão são registradas como erros.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A>|Parâmetro `String` opcional.<br /><br /> Importância para fazer o texto do fluxo de saída o padrão.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A>|Parâmetro `String` opcional.<br /><br /> Importância para fazer o texto do fluxo de saída o padrão.|  
|<xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A>|Virtual opcional `Int32` parâmetro.<br /><br /> Especifica a quantidade de tempo, em milissegundos, após o qual a tarefa executável é encerrada.  O valor padrão é `Int.MaxValue`, indicando que não há nenhum período de tempo limite. Tempo limite é em milissegundos.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A>|Virtual opcional `string` parâmetro.<br /><br /> Projetos podem implementar esta opção para substituir um nome da ferramenta.  Tarefas podem substituir essa opção para preservar o nome da ferramenta.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A>|Parâmetro `string` opcional.<br /><br /> Especifica o local de onde a tarefa carrega o arquivo executável subjacente.  Se esse parâmetro não for especificado, a tarefa usa o caminho de instalação do SDK que corresponde à versão do framework que está executando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|<xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A>|Parâmetro `bool` opcional.<br /><br /> Quando definido como `true`, essa tarefa cria um arquivo de lote para a linha de comando e o executa usando o processador de comando em vez de executar o comando diretamente.|  
|<xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A>|Parâmetro `bool` opcional.<br /><br /> Quando definido como `true`, essa tarefa gera o nó quando a tarefa estiver em execução.|  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)