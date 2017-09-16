---
title: "Compilando vários projetos paralelamente com o MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
caps.latest.revision: 20
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
ms.translationtype: HT
ms.sourcegitcommit: 17defdd0b96ec1c3273fc6b845af844b031a4a17
ms.openlocfilehash: 6aa02abdbfe8ea55b6e3434dbc859b5fa5d6a5e3
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="building-multiple-projects-in-parallel-with-msbuild"></a>Compilando vários projetos paralelamente com o MSBuild
Você pode usar o MSBuild para criar vários projetos mais rápido, executando-os em paralelo. Para executar compilações em paralelo, você pode usar as seguintes configurações em um computador com processador de vários núcleos ou vários processadores:  
  
-   Opção `/maxcpucount` em um prompt de comando.  
  
-   O parâmetro de tarefa <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> em uma tarefa do MSBuild.  
  
> [!NOTE]
>  A opção **/verbosity** (**/v**) em uma linha de comando também pode afetar o desempenho de compilação. O desempenho de compilação pode piorar se o detalhamento de suas informações de log de compilação estiver definido como detalhado ou diagnóstico, que são usados para solução de problemas. Para obter mais informações, consulte [Obtendo logs de compilação](../msbuild/obtaining-build-logs-with-msbuild.md) e [Referências de linha de comando](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="maxcpucount-switch"></a>Opção /maxcpucount  
 Se você usar a opção `/maxcpucount`, ou `/m`, de forma abreviada, o MSBuild cria o número especificado de processos MSBuild.exe que podem ser executados em paralelo. Esses processos também são conhecidos como "processos de trabalho". Cada processo de trabalho usa um núcleo ou processador separado, se houver algum disponível, para compilar um projeto ao mesmo tempo em que outros processadores disponíveis criam outros. Por exemplo, definir essa opção para um valor de "4" faz com que o MSBuild crie quatro processos de trabalho para compilar o projeto.  
  
 Se você incluir a opção `/maxcpucount` sem especificar um valor, o MSBuild usará o número de processadores no computador.  
  
 Para obter mais informações sobre essa opção, que foi introduzida no MSBuild 3.5, consulte [Referências de linha de comando](../msbuild/msbuild-command-line-reference.md).  
  
 O exemplo a seguir instrui o MSBuild a usar três processos de trabalho. Se você usar essa configuração, o MSBuild pode compilar três projetos ao mesmo tempo.  
  
```  
msbuild.exe myproj.proj /maxcpucount:3  
```  
  
## <a name="buildinparallel-task-parameter"></a>Parâmetro de Tarefa BuildInParallel  
 `BuildInParallel` é um parâmetro booliano opcional em uma tarefa [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Quando `BuildInParallel` é definido como `true` (seu valor padrão é `false`), vários processos de trabalho são gerados para compilar tantos projetos quanto possível ao mesmo tempo. Para que isso funcione corretamente, a opção `/maxcpucount` deve ser definida como um valor maior que 1, e o sistema deve ser pelo menos de dois núcleos ou ter dois ou mais processadores.  
  
 A seguir está um exemplo, retirado de microsoft.common.targets, sobre como definir o parâmetro `BuildInParallel`.  
  
```  
<PropertyGroup>  
    <BuildInParallel Condition="'$(BuildInParallel)' ==   
        ''">true</BuildInParallel>  
</PropertyGroup>  
<MSBuild  
    Projects="@(_MSBuildProjectReferenceExistent)"  
    Targets="GetTargetPath"  
    BuildInParallel="$(BuildInParallel)"  
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);   
        %(_MSBuildProjectReferenceExistent.SetPlatform)"  
    Condition="'@(NonVCProjectReference)'!='' and   
        ('$(BuildingSolutionFile)' == 'true' or   
        '$(BuildingInsideVisualStudio)' == 'true' or   
        '$(BuildProjectReferences)' != 'true') and     
        '@(_MSBuildProjectReferenceExistent)' != ''"  
    ContinueOnError="!$(BuildingProject)">  
    <Output TaskParameter="TargetOutputs"   
        ItemName="_ResolvedProjectReferencePaths"/>  
</MSBuild>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando vários processadores para compilar projetos](../msbuild/using-multiple-processors-to-build-projects.md)   
 [Escrevendo agentes com reconhecimento de multiprocessador](../msbuild/writing-multi-processor-aware-loggers.md)   
 [Blog: Ajustando o paralelismo de compilação do C++](http://go.microsoft.com/fwlink/?LinkId=251457)

