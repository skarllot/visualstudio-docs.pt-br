---
title: "Tarefa Exec | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Exec"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "tarefa Exec [MSBuild]"
  - "MSBuild, tarefa Exec"
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa Exec
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Executa o programa ou comando especificado, usando os argumentos especificados.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros para o `Exec` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Command`|Obrigatório `String` parâmetro.<br /><br /> Os comandos para executar.  Eles podem ser os comandos do sistema, como, por exemplo, attrib, ou um executável, como o programa. exe, runprogram.bat ou Setup. msi.<br /><br /> Este parâmetro pode conter várias linhas de comandos.  Como alternativa, você pode colocar vários comandos em um arquivo em lotes e executá\-lo usando esse parâmetro.|  
|`CustomErrorRegularExpression`|Opcional `String` parâmetro.<br /><br /> Especifica uma expressão regular que é usada para linhas especiais de erro na saída da ferramenta.  Isso é útil para ferramentas que produzem saída formatada incomum.|  
|`CustomWarningRegularExpression`|Opcional `String` parâmetro.<br /><br /> Especifica uma expressão regular que é usada para linhas especiais de aviso na saída da ferramenta.  Isso é útil para ferramentas que produzem saída formatada incomum.|  
|`ExitCode`|Opcional `Int32` somente leitura parâmetro de saída.<br /><br /> Especifica o código de saída fornecida pelo comando executado.|  
|`IgnoreExitCode`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, a tarefa ignora o código de saída fornecida pelo comando executado.  Caso contrário, a tarefa retorna `false` se o comando executado retorna um código de saída diferente de zero.|  
|`IgnoreStandardErrorWarningFormat`|Opcional `Boolean` parâmetro.<br /><br /> Se `false`, seleciona linhas na saída que correspondem ao formato de aviso\/erro padrão e os registra em log como erros\/avisos.  Se `true`, desativar esse comportamento.|  
|`Outputs`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém os itens de saída da tarefa.  O `Exec` tarefa não define essas propriamente dito.  Em vez disso, você pode fornecê\-los como se ela definida\-los, para que eles podem ser usados posteriormente no projeto.|  
|`StdErrEncoding`|Opcional `String` parâmetro de saída.<br /><br /> Especifica a codificação do fluxo de erro padrão tarefa capturados.  O padrão é o atual console codificação de saída.|  
|`StdOutEncoding`|Opcional `String` parâmetro de saída.<br /><br /> Especifica a codificação do fluxo de saída padrão tarefa capturados.  O padrão é o atual console codificação de saída.|  
|`WorkingDirectory`|Opcional `String` parâmetro.<br /><br /> Especifica o diretório no qual o comando será executado.|  
  
## Comentários  
 Esta tarefa é útil quando um determinado [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] de tarefas para o trabalho que você deseja executar não está disponível.  No entanto, o `Exec` tarefa, ao contrário de uma tarefa mais específica, não é possível reunir a saída da ferramenta ou comando que ele seja executado.  
  
 O `Exec` tarefa chama o cmd. exe em vez de chamar diretamente de um processo.  
  
 Com os parâmetros listados neste documento, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.ToolTaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.ToolTask> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe ToolTaskExtension \(base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a `Exec` tarefa para executar um comando.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)