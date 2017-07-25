---
title: Como compilar um projeto que tem recursos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 14
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 641697cabee22a86e3b5ee7a360cbea154ead486
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---
# <a name="how-to-build-a-project-that-has-resources"></a>Como compilar um projeto que tem recursos
Se você estiver compilando versões localizadas de um projeto, todos os elementos da interface do usuário devem ser separados em arquivos de recursos para os diferentes idiomas. Se o projeto usar somente cadeias de caracteres, os arquivos de recursos poderão usar arquivos de texto. Uma alternativa é usar arquivos .resx como os arquivos de recurso.  
  
## <a name="compiling-resources-with-msbuild"></a>Compilando recursos com o MSBuild  
 A biblioteca de tarefas comuns fornecida com o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] inclui uma tarefa `GenerateResource` que você pode usar para compilar recursos em arquivos .resx ou de texto. Esta tarefa inclui o parâmetro `Sources` para especificar quais arquivos de recurso compilar e o parâmetro `OutputResources` para especificar nomes para os arquivos de recurso de saída. Para obter mais informações sobre a tarefa `GenerateResource`, consulte [Tarefa GenerateResource](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Para compilar recursos com o MSBuild  
  
1.  Identifique os arquivos de recurso do projeto e passe-os para a tarefa `GenerateResource`, como listas de itens ou como nomes de arquivo.  
  
2.  Especifique o parâmetro `OutputResources` da tarefa `GenerateResource`, que permite que você defina os nomes para os arquivos de recurso de saída.  
  
3.  Use o elemento `Output` da tarefa para armazenar o valor do parâmetro `OutputResources` em um item.  
  
4.  Use o item criado do elemento `Output` como uma entrada em outra tarefa.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como o elemento `Output` especifica que o atributo `OutputResources` da tarefa `GenerateResource` conterá os arquivos de recurso compilados `alpha.resources` e `beta.resources` e que esses dois arquivos serão colocados dentro da lista de itens `Resources`. Identificando esses arquivos de recursos como uma coleção de itens de mesmo nome, você poderá facilmente usá-los como entradas para outra tarefa, como a tarefa [Csc](../msbuild/csc-task.md).  
  
 Essa tarefa é equivalente a usar o comutador **/compile** para [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```xml  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de projeto a seguir contém duas tarefas: a tarefa `GenerateResource` para compilar recursos e a tarefa `Csc` para compilar os arquivos de código-fonte e os arquivos de recurso compilados. Os arquivos de recurso compilados pela tarefa `GenerateResource` são armazenados no item `Resources` e passados para a tarefa `Csc`.  
  
```xml  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
[MSBuild](../msbuild/msbuild.md)  
 [Tarefa GenerateResource](../msbuild/generateresource-task.md)   
 [Tarefa Csc](../msbuild/csc-task.md)   
 [Resgen.exe (Gerador de Arquivo de Recurso)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
