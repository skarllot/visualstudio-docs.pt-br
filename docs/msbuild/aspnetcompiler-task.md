---
title: "Tarefa AspNetCompiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa AspNetCompiler [MSBuild]"
  - "MSBuild, Tarefa AspNetCompiler"
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa AspNetCompiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O `AspNetCompiler` tarefa envolve Aspnet\_compiler. exe, um utilitário para pré\-compilar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativos.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `AspNetCompiler` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AllowPartiallyTrustedCallers`|Opcional `Boolean` parâmetro.<br /><br /> Se este parâmetro for `true`, o assembly de nome forte permitirá que os chamadores parcialmente confiáveis.|  
|`Clean`|Opcional `Boolean` parâmetro<br /><br /> Se este parâmetro for `true`, o aplicativo pré\-compilado será compilado limpa.  Todos os componentes compilados anteriormente sejam recompilados.  O valor padrão é `false`.  Este parâmetro corresponde do **\-c** ligar Aspnet\_compiler. exe.|  
|`Debug`|Opcional `Boolean` parâmetro.<br /><br /> Se este parâmetro for `true`, informações de depuração \(.O arquivo PDB\) é emitido durante a compilação.  O valor padrão é `false`.  Este parâmetro corresponde do **\-d** ligar Aspnet\_compiler. exe.|  
|`DelaySign`|Opcional `Boolean` parâmetro.<br /><br /> Se este parâmetro for `true`, o assembly não é totalmente assinado quando criado.|  
|`FixedNames`|Opcional `Boolean` parâmetro.<br /><br /> Se este parâmetro for `true`, os assemblies compilados receberão nomes fixos..|  
|`Force`|Opcional `Boolean` parâmetro<br /><br /> Se este parâmetro for `true`, a tarefa irá substituir o diretório de destino se ele já existir.  Conteúdos existentes são perdidos.  O valor padrão é `false`.  Este parâmetro corresponde do **\-f** ligar Aspnet\_compiler. exe.|  
|`KeyContainer`|Opcional `String` parâmetro.<br /><br /> Especifica um contêiner de chave de nome forte.|  
|`KeyFile`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho físico para o arquivo de chave de nome de alta segurança..|  
|`MetabasePath`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho completo da metabase do IIS do aplicativo.  Este parâmetro não pode ser combinado com o `VirtualPath` ou `PhysicalPath` parâmetros.  Este parâmetro corresponde do **\-m** ligar Aspnet\_compiler. exe.|  
|`PhysicalPath`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho físico do aplicativo para ser compilado.  Se este parâmetro estiver ausente, a metabase do IIS é usado para localizar o aplicativo.  Este parâmetro corresponde do **\-p** ligar Aspnet\_compiler. exe.|  
|`TargetFrameworkMoniker`|Opcional `String` parâmetro.<br /><br /> Especifica o TargetFrameworkMoniker indicando qual.NET Framework versão Aspnet\_compiler. exe deve ser usada.  Só aceita.Identificadores de origem do NET Framework.|  
|`TargetPath`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho físico para o qual o aplicativo é compilado.  Se não especificado, o aplicativo é pré\-compilado no local.|  
|`Updateable`|Opcional `Boolean` parâmetro.<br /><br /> Se este parâmetro for `true`, o aplicativo pré\-compilado será atualizável.  O valor padrão é `false`.  Este parâmetro corresponde do **\-u** ligar Aspnet\_compiler. exe.|  
|`VirtualPath`|Opcional `String` parâmetro.<br /><br /> O caminho virtual do aplicativo para ser compilado.  Se `PhysicalPath` especificado, o caminho físico é usado para localizar o aplicativo.  Caso contrário, a metabase do IIS é usado e o aplicativo será considerado no site padrão.  Este parâmetro corresponde do **\-v** ligar Aspnet\_compiler. exe.|  
  
## Comentários  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.ToolTaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.ToolTask> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe ToolTaskExtension \(base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Exemplo  
 O seguinte exemplo de código usa a `AspNetCompiler` tarefas para pré\-compilar um [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)