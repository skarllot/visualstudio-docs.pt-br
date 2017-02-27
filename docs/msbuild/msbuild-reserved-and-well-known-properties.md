---
title: Propriedades reservadas e conhecidas do MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 29
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 078576d6e1988bf1cefbb09646ea44f61085f5cf

---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propriedades reservadas e conhecidas do MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornece um conjunto de propriedades predefinidas que armazenam informações sobre o arquivo de projeto e os binários [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Essas propriedades são avaliadas da mesma maneira que outras propriedades [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Por exemplo, para usar a propriedade `MSBuildProjectFile`, digite `$(MSBuildProjectFile)`.  
  
 O MSBuild usa os valores na tabela a seguir para predefinir propriedades conhecidas e reservadas. As propriedades reservadas não podem ser substituídas, mas as propriedades conhecidas podem ser substituídas usando propriedades de ambiente com o mesmo nome, propriedades globais ou propriedades que são declaradas no arquivo de projeto.  
  
## <a name="reserved-and-well-known-properties"></a>Propriedades reservadas e conhecidas  
 A tabela a seguir descreve as propriedades predefinidas [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
|Propriedade|Descrição|Reservadas ou conhecidas|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|O caminho absoluto da pasta em que os binários [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que estão sendo usados no momento estão localizados (por exemplo, C:\Windows\Microsoft.Net\Framework\\*versionNumber*). Essa propriedade será útil se você precisar fazer referência a arquivos no diretório [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> Não inclua a barra invertida final nessa propriedade.|Reservado|  
|`MSBuildExtensionsPath`|Apresentado no .NET Framework 4: não há diferença entre os valores padrão de `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`. Você pode definir a variável de ambiente `MSBUILDLEGACYEXTENSIONSPATH` como um valor não nulo para habilitar o comportamento do valor padrão de `MSBuildExtensionsPath` em versões anteriores.<br /><br /> No .NET Framework 3.5 e versões anteriores, o valor padrão de `MSBuildExtensionsPath` aponta para o caminho da subpasta MSBuild na pasta \Program Files\ ou \Program Files (x86), dependendo do número de bits do processo atual. Por exemplo, para um processo de 32 bits em um computador de 64 bits, essa propriedade aponta para a pasta \Program Files (x86). Para um processo de 64 bits em um computador de 64 bits, essa propriedade aponta para a pasta \Program Files.<br /><br /> Não inclua a barra invertida final nessa propriedade.<br /><br /> Esse local é um local útil para colocar os arquivos de destino personalizados. Por exemplo, os arquivos de destino poderiam ser instalados em \Program Files\MSBuild\MyFiles\Northwind.targets e importados em arquivos de projeto usando esse código XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Conhecidas|  
|`MSBuildExtensionsPath32`|O caminho da subpasta [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] na pasta \Program Files ou \Program Files (x86). Esse caminho sempre aponta para a pasta de 32 bits \Program Files em um computador de 32 bits e \Program Files (x86) em um computador de 64 bits. Consulte também `MSBuildExtensionsPath` e `MSBuildExtensionsPath64`.<br /><br /> Não inclua a barra invertida final nessa propriedade.|Conhecidas|  
`MSBuildExtensionsPath64`|O caminho da subpasta [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] na pasta \Program Files. Para uma máquina de 64 bits, esse caminho sempre aponta para a pasta \Program Files. Para uma máquina de 32 bits, esse caminho fica em branco. Consulte também `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`.<br /><br /> Não inclua a barra invertida final nessa propriedade.|Conhecidas|  
|`MSBuildLastTaskResult`|`true` se a tarefa anterior foi concluída sem erros (mesmo se houver avisos) ou `false` se a tarefa anterior tiver erros. Normalmente, quando ocorre um erro em uma tarefa, o erro é a última coisa que ocorre nesse projeto. Portanto, o valor dessa propriedade nunca é `false`, exceto nestes cenários:<br /><br /> - Quando o atributo `ContinueOnError` do [elemento Task (MSBuild)](../msbuild/task-element-msbuild.md) é definido como `WarnAndContinue` (ou `true`) ou `ErrorAndContinue`.<br /><br /> - Quando o `Target` tem um [elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) como um elemento filho.|Reservado|  
|`MSBuildNodeCount`|O número máximo de processos simultâneos que são usados durante a compilação. Esse é o valor especificado para **/maxcpucount** na linha de comando. Se você especificou **/maxcpucount** sem especificar um valor, então `MSBuildNodeCount` especificará o número de processadores no computador. Para obter mais informações, consulte [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md) e [Criando vários projetos paralelamente](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Reservado|  
|`MSBuildProgramFiles32`|O local da pasta do programa de 32 bits; por exemplo, `C:\Program Files (x86)`.<br /><br /> Não inclua a barra invertida final nessa propriedade.|Reservado|  
|`MSBuildProjectDefaultTargets`|A lista completa de destinos que estão especificados no atributo `DefaultTargets` do elemento `Project`. Por exemplo, o seguinte elemento `Project` teria um valor da propriedade `MSBuildDefaultTargets` de `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Reservado|  
|`MSBuildProjectDirectory`|O caminho absoluto do diretório em que o arquivo de projeto está localizado, por exemplo `C:\MyCompany\MyProduct`.<br /><br /> Não inclua a barra invertida final nessa propriedade.|Reservado|  
|`MSBuildProjectDirectoryNoRoot`|O valor da propriedade `MSBuildProjectDirectory`, excluindo a unidade raiz.<br /><br /> Não inclua a barra invertida final nessa propriedade.|Reservado|  
|`MSBuildProjectExtension`|A extensão de nome de arquivo do arquivo de projeto, incluindo o período; por exemplo,. proj.|Reservado|  
|`MSBuildProjectFile`|O nome de arquivo completo do arquivo de projeto, incluindo a extensão de nome de arquivo; por exemplo, MyApp.proj.|Reservado|  
|`MSBuildProjectFullPath`|O caminho absoluto e o nome de arquivo completo do arquivo de projeto, incluindo a extensão de nome de arquivo; por exemplo, C:\MyCompany\MyProduct\MyApp.proj.|Reservado|  
|`MSBuildProjectName`|O nome de arquivo do arquivo de projeto sem a extensão de nome de arquivo; por exemplo, MyApp.|Reservado|  
|`MSBuildStartupDirectory`|O caminho absoluto da pasta em que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] é chamado. Usando essa propriedade, você pode compilar tudo abaixo de um ponto específico em uma árvore de projeto sem criar arquivos dirs.proj em cada diretório. Em vez disso, você tem apenas um projeto — por exemplo, c:\traversal.proj, como mostrado aqui:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Para compilar em qualquer ponto da árvore, digite:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Não inclua a barra invertida final nessa propriedade.|Reservado|  
|`MSBuildThisFile`|O nome do arquivo e a parte da extensão do arquivo de `MSBuildThisFileFullPath`.|Reservado|  
|`MSBuildThisFileDirectory`|A parte do diretório de `MSBuildThisFileFullPath`.<br /><br /> Inclua a barra invertida final no caminho.|Reservado|  
|`MSBuildThisFileDirectoryNoRoot`|A parte do diretório de `MSBuildThisFileFullPath`, excluindo a unidade raiz.<br /><br /> Inclua a barra invertida final no caminho.|Reservado|  
|`MSBuildThisFileExtension`|A parte da extensão do nome de arquivo de `MSBuildThisFileFullPath`.|Reservado|  
|`MSBuildThisFileFullPath`|O caminho absoluto do projeto ou do arquivo de destinos que contém o destino que está sendo executado.<br /><br /> Dica: você pode especificar um caminho relativo em um arquivo de destino que é relativo ao arquivo de destino e não relativo ao arquivo de projeto original.|Reservado|  
|`MSBuildThisFileName`|A parte do nome de arquivo de `MSBuildThisFileFullPath`, sem a extensão de nome de arquivo.|Reservado|  
|`MSBuildToolsPath`|O caminho de instalação da versão [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] associada ao valor de `MSBuildToolsVersion`.<br /><br /> Não inclua a barra invertida final no caminho.<br /><br /> Essa propriedade não pode ser substituída.|Reservado|  
|`MSBuildToolsVersion`|A versão do Conjunto de ferramentas [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que é usado para compilar o projeto.<br /><br /> Observação: um conjunto de ferramentas [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] consiste em tarefas, destinos e ferramentas que são usados para compilar um aplicativo. As ferramentas incluem compiladores, tais como csc.exe e vbc.exe. Para obter mais informações, consulte [Conjunto de ferramentas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) e [Configurações padrão e personalizada do conjunto de ferramentas](../msbuild/standard-and-custom-toolset-configurations.md).|Reservado|  
  
## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md)
 [Propriedades do MSBuild](../msbuild/msbuild-properties.md)


<!--HONumber=Feb17_HO4-->


