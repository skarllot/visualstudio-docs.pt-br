---
title: "Tarefa WriteCodeFragment | Microsoft Docs"
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
  - "MSBuild, Tarefa WriteCodeFragment"
  - "Tarefa WriteCodeFragment [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa WriteCodeFragment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gera um arquivo de código temporário do fragmento de código gerado especificado.  Não exclua o arquivo.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `WriteCodeFragment` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`AssemblyAttributes`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Descrição dos atributos de escrever.  O item `Include` o valor é o nome de tipo completo of o atributo, por exemplo, "System.AssemblyVersionAttribute".<br /><br /> Cada metadados são o par de nome\-valor de um parâmetro, que deve ser do tipo `String`.  Alguns atributos só permitem que os argumentos do construtor posicional.  No entanto, você pode usar esses argumentos em qualquer atributo.  Para definir os atributos de construtor posicional, use nomes de metadados que se assemelhem a "\_Parameter1", "\_Parameter2" e assim por diante.<br /><br /> O índice de parâmetros não pode ser ignorado.|  
|`Language`|Obrigatório `String` parâmetro.<br /><br /> Especifica o idioma do código para gerar.<br /><br /> `Language`pode ser qualquer idioma para o qual um provedor de CodeDom estiver disponível, por exemplo, "C\#" ou "VisualBasic".  O arquivo emitido terá a extensão de nome de arquivo padrão para esse idioma.|  
|`OutputDirectory`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica a pasta de destino para o código gerado, geralmente a pasta intermediário.|  
|`OutputFile`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro de saída.<br /><br /> Especifica o caminho do arquivo que foi gerado.  Se esse parâmetro é definido usando um nome de arquivo, a pasta de destino é anexada ao nome do arquivo.  Se ele é definido por meio de uma raiz, a pasta de destino será ignorada.<br /><br /> Se este parâmetro não for definido, o nome do arquivo de saída é a pasta de destino, um nome de arquivo arbitrário e a extensão de nome de arquivo padrão para o idioma especificado.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)