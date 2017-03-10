---
title: "Tarefa SGen | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#SGen"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, tarefa SGen"
  - "tarefa SGen [MSBuild]"
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa SGen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cria um assembly de serialização XML para tipos no assembly especificado.  Esta tarefa envolve a ferramenta XML Serializer Generator \(Sgen. exe\).  Para mais informações, consulte [XML Serializer Generator Tool \(Sgen.exe\)](../Topic/XML%20Serializer%20Generator%20Tool%20\(Sgen.exe\).md).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros do `SGen` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`BuildAssemblyName`|Obrigatório `String` parâmetro.<br /><br /> O assembly para gerar código de serialização.|  
|`BuildAssemblyPath`|Obrigatório `String` parâmetro.<br /><br /> O caminho para o assembly para gerar código de serialização.|  
|`DelaySign`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, especifica que um assembly totalmente assinado.  Se `false`, especifica que você deseja colocar a chave pública do assembly apenas.<br /><br /> Este parâmetro não terá efeito a menos que usado com um a `KeyFile` ou `KeyContainer` parâmetro.|  
|`KeyContainer`|Opcional `String` parâmetro.<br /><br /> Especifica um contêiner que contém um par de chaves.  Isso assinará o assembly inserindo uma chave pública no manifesto do assembly.  A tarefa, em seguida, irá assinar o assembly final com a chave particular.|  
|`KeyFile`|Opcional `String` parâmetro.<br /><br /> Especifica um par de chaves ou uma chave pública para usar para assinar um assembly.  O compilador insere a chave pública no manifesto do assembly e assina o assembly final com a chave particular.|  
|`Platform`|Opcional `String` parâmetro.<br /><br /> Obtém ou define a plataforma de compilador usado para gerar o assembly de saída.  Este parâmetro pode ter um valor de `x86`, `x64`, ou `anycpu`.  O padrão é `anycpu`.|  
|`References`|Opcional `String[]` parâmetro.<br /><br /> Especifica os assemblies referenciados pelos tipos exigindo a serialização de XML.|  
|`SdkToolsPath`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho para as ferramentas do SDK, como, por exemplo, Resgen. exe.|  
|`SerializationAssembly`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém o assembly de serialização gerado.|  
|`SerializationAssemblyName`|Opcional `String` parâmetro.<br /><br /> Especifica o nome do assembly de serialização gerado.|  
|`ShouldGenerateSerializer`|Obrigatório `Boolean` parâmetro.<br /><br /> Se `true`, a tarefa SGen deve gerar um assembly de serialização.|  
|`Timeout`|Opcional `Int32` parâmetro.<br /><br /> Especifica a quantidade de tempo, em milissegundos, após o qual a tarefa executável é encerrada.  O valor padrão é `Int.MaxValue`, indicando que não há nenhum período de tempo limite.|  
|`ToolPath`|Opcional `String` parâmetro.<br /><br /> Especifica o local de onde a tarefa carregará o arquivo executável subjacente \(Sgen. exe\).  Se este parâmetro não for especificado, a tarefa usa o caminho de instalação do SDK correspondente à versão do framework que está executando o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Types`|Opcional `String[]` parâmetro.<br /><br /> Obtém ou define uma lista de tipos específicos para gerar código de serialização.  SGen irá gerar o código de serialização somente para esses tipos.|  
|`UseProxyTypes`|Obrigatório `Boolean` parâmetro.<br /><br /> Se `true`, a tarefa SGen gera código de serialização somente para os tipos de proxy do serviço XML da Web.|  
  
## Comentários  
 Além para os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.ToolTaskExtension> classe, que herda de <xref:Microsoft.Build.Utilities.ToolTask> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe ToolTaskExtension \(base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)