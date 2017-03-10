---
title: Tarefa CreateItem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateItem
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateItem task [MSBuild]
- MSBuild, CreateItem task
ms.assetid: c4311f38-979e-4324-b524-9e8c1cbdc41a
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: a9eb48e8c695c92a68e75f17cea31d887dfb439d
ms.lasthandoff: 02/22/2017

---
# <a name="createitem-task"></a>Tarefa CreateItem
Popula as coleções de itens com os itens de entrada. Isso permite que os itens sejam copiados de uma lista para outra.  
  
> [!NOTE]
>  Essa tarefa foi preterida. Do .NET Framework 3.5 em diante, grupos de itens podem ser colocados dentro de elementos [Target](../msbuild/target-element-msbuild.md). Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).  
  
## <a name="attributes"></a>Atributos  
 A tabela a seguir descreve os parâmetros da tarefa `CreateItem`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AdditionalMetadata`|Parâmetro de matriz `String` opcional.<br /><br /> Especifica os metadados adicionais para anexar aos itens de saída.  Especifique o nome de metadados e o valor do item com a seguinte sintaxe:<br /><br /> *MetadataName* `=` *MetadataValue*<br /><br /> Vários pares de nome/valor de metadados devem ser separados por ponto e vírgula. Se o nome ou o valor contiver um ponto e vírgula ou outros caracteres especiais, eles devem ser escapados. Para obter mais informações, consulte [Como escapar caracteres especiais no MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).|  
|`Exclude`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica os itens a serem excluídos da coleção de itens de saída. Esse parâmetro pode conter especificações de curinga. Para mais informações, consulte [Itens](../msbuild/msbuild-items.md) e [Como excluir arquivos do build](../msbuild/how-to-exclude-files-from-the-build.md).|  
|`Include`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]`necessário.<br /><br /> Especifica os itens a serem incluídos na coleção de itens de saída. Esse parâmetro pode conter especificações de curinga.|  
|`PreserveExistingMetadata`|Parâmetro `Boolean` opcional.<br /><br /> Se `True`, somente os metadados adicionais se aplicarão, se eles ainda não existirem.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir cria um novo item denominado `MySourceItemsWithMetadata` da coleção de itens `MySourceItems`. A tarefa `CreateItem` popula a nova coleção de itens com os itens no item `MySourceItems`. Em seguida, ela adiciona uma entrada de metadados adicionais chamada `MyMetadata` com um valor de `Hello` para cada item na nova coleção.  
  
 Depois que a tarefa é executada, a coleção de itens `MySourceItemsWithMetadata` contém os itens `file1.resx` e `file2.resx`, ambos com entradas de metadados para `MyMetadata`. A coleta do item `MySourceItems` permanece inalterada.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceItems Include="file1.resx;file2.resx" />  
    </ItemGroup>  
  
    <Target Name="NewItems">  
        <CreateItem  
            Include="@(MySourceItems)"  
            AdditionalMetadata="MyMetadata=Hello">  
           <Output  
               TaskParameter="Include"  
               ItemName="MySourceItemsWithMetadata"/>  
        </CreateItem>  
  
    </Target>  
  
</Project>  
```  
  
 A tabela a seguir descreve o valor do item de saída após a execução da tarefa. Os metadados de item são mostrados entre parênteses após o item.  
  
|Coleta de itens|Conteúdo|  
|---------------------|--------------|  
|`MySourceItemsWithMetadata`|`file1.resx` (`MyMetadata="Hello"`)<br /><br /> `file2.resx` (`MyMetadata="Hello"`)|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)
