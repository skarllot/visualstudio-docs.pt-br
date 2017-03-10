---
title: "Tarefa RegisterAssembly | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Tarefa RegisterAssembly"
  - "Tarefa RegisterAssembly [MSBuild]"
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa RegisterAssembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ler metadados do assembly especificado e adiciona as entradas necessárias ao Registro, que permite que os clientes COM criar classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] transparente.  O comportamento de esta tarefa é semelhante, mas não idêntico, a de [Regasm.exe \(Ferramenta de Registro de Assembly\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros de tarefa de `RegisterAssembly` .  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Assemblies`|Parâmetro necessário <xref:Microsoft.Build.Framework.ITaskItem>de`[]` .<br /><br /> Especifica os assemblies sejam registrados com COM.|  
|`AssemblyListFile`|Parâmetro opcional de <xref:Microsoft.Build.Framework.ITaskItem> .<br /><br /> Contém informações sobre o estado entre a tarefa de `RegisterAssembly` e a tarefa de [UnregisterAssembly](../msbuild/unregisterassembly-task.md) .  Isso impede que a tarefa de `UnregisterAssembly` tente ao unregister um assembly que não tenha sido registrado na tarefa de `RegisterAssembly` .|  
|`CreateCodeBase`|Parâmetro opcional de `Boolean` .<br /><br /> Se `true`, cria uma entrada da no Registro, especificando o caminho de arquivo para um assembly que não está instalado no cache global de assemblies.  Você não deve especificar esta opção se você fosse subseqüentemente o assembly que você estar inscrevendo na cache global de assemblies.|  
|`TypeLibFiles`|Parâmetro de saída opcional de <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Especifica a biblioteca de tipos para gerar do assembly especificado.  A biblioteca de tipo gerado contém definições de tipos definidos acessíveis dentro do assembly.  A biblioteca de tipos é gerada somente se uma das seguintes for verdadeira:<br /><br /> -   Uma biblioteca de tipo de aquele nome não existe em aquele local.<br />-   Uma biblioteca de tipo existe mas é mais antiga do que o assembly que está sendo passado.<br /><br /> Se a biblioteca de tipos é mais recente que o assembly que está sendo passado, um novo não será criado, mas o assembly será registrado ainda.<br /><br /> Se o parâmetro for especificado, deve ter o mesmo número de itens como o parâmetro de `Assemblies` ou a tarefa irão falhar.  Se nenhuma entrada for especificada, a tarefa usará como padrão o nome do assembly e alterará a extensão de item a .tlb.|  
  
## Comentários  
 Além dos parâmetros listados acima, esta tarefa parâmetros herda da classe de <xref:Microsoft.Build.Tasks.TaskExtension> própria, que herda da classe de <xref:Microsoft.Build.Utilities.Task> .  Para obter uma lista de esses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a tarefa de `RegisterAssembly` registrar o assembly especificado pela coleção de item de `MyAssemblies` .  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)