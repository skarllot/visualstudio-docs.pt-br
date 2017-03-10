---
title: "Tarefa WriteLinesToFile | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Tarefa WriteLinesToFile"
  - "Tarefa WriteLinesToFile [MSBuild]"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa WriteLinesToFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grava os caminhos dos itens especificados no arquivo de texto especificado.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `WriteLinestoFile` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`File`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o arquivo para gravar os itens.|  
|`Lines`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os itens para gravar no arquivo.|  
|`Overwrite`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, a tarefa substitui qualquer conteúdo existente no arquivo.|  
|`Encoding`|Opcional `String` parâmetro.<br /><br /> Seleciona o caractere de codificação, por exemplo, "Unicode".  See also <xref:System.Text.Encoding>.|  
  
## Comentários  
 Se `Overwrite` é `true`, cria um novo arquivo, gravar o conteúdo no arquivo e, em seguida, fecha o arquivo.  Se o arquivo de destino já existir, ele será sobrescrito.  Se `Overwrite` é `false`, acrescenta o conteúdo para o arquivo, criando o arquivo de destino se ele ainda não existir.  
  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a `WriteLinesToFile` tarefa de escrever os caminhos dos itens na `MyItems` item da coleção para o arquivo especificado pelo `MyTextFile` item da coleção.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)