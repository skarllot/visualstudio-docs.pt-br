---
title: Como configurar destinos e tarefas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
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
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>Como configurar destinos e tarefas
Tarefas do MSBuild selecionadas podem ser definidas para serem executadas no ambiente de destino, independentemente do ambiente do computador de desenvolvimento. Por exemplo, quando você usa um computador de 64 bits para criar um aplicativo destinado a uma arquitetura de 32 bits, as tarefas selecionadas são executadas em um processo de 32 bits.  
  
> [!NOTE]
>  Se uma tarefa de build é escrita em uma linguagem .NET como Visual C# ou Visual Basic e essa tarefa não usa recursos nativos nem ferramentas, ela será executada em qualquer contexto de destino sem adaptação.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>Parâmetros de tarefa e atributos UsingTask  
 Os atributos `UsingTask` a seguir afetam todas as operações de uma tarefa em um processo de build específico:  
  
-   O atributo `Runtime`, se presente, define a versão do CLR (Common Language Runtime) e pode assumir qualquer um destes valores: `CLR2`, `CLR4`, `CurrentRuntime` ou `*` (qualquer tempo de execução).  
  
-   O atributo `Architecture`, se presente, define a plataforma e o número de bit e pode assumir qualquer um destes valores: `x86`, `x64`, `CurrentArchitecture` ou `*` (qualquer arquitetura).  
  
-   O atributo `TaskFactory`, se presente, define a fábrica de tarefas que cria e executa a instância de tarefa e usa apenas o valor `TaskHostFactory`. Para obter mais informações, consulte a seção Fábricas de Tarefas mais adiante neste documento.  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Você também pode usar os parâmetros `MSBuildRuntime` e `MSBuildArchitecture` para definir o contexto de destino de uma tarefa individual.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Antes do MSBuild executar uma tarefa, ele procura uma correspondência `UsingTask` que tem o mesmo contexto de destino.  Parâmetros especificados no `UsingTask` mas não na tarefa correspondente são considerados com correspondência.  Parâmetros especificados na tarefa mas não no `UsingTask` correspondente também são considerados com correspondência. Se os valores de parâmetro não forem especificados no `UsingTask` nem na tarefa, os valores assumem o valor `*` por padrão (qualquer parâmetro).  
  
> [!WARNING]
>  Se mais de um `UsingTask` existe e todos têm atributos `TaskName`, `Runtime` e `Architecture` correspondentes, o último a ser avaliado substitui os outros.  
  
 Se os parâmetros são definidos na tarefa, o MSBuild tenta encontrar um `UsingTask` que corresponde a esses parâmetros ou que, pelo menos, não está em conflito com eles.  Mais de um `UsingTask` pode especificar o contexto de destino da mesma tarefa.  Por exemplo, uma tarefa com executáveis diferentes para ambientes de destino diferentes pode ser semelhante a esta:  
  
```xml  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>Fábricas de tarefa  
 Antes de executar uma tarefa, o MSBuild verifica para ver se ela é designada para ser executada no contexto do software atual.  Se a tarefa for designada desse modo, o MSBuild a passará para AssemblyTaskFactory, que a executará no processo atual; caso contrário, o MSBuild passará a tarefa para TaskHostFactory, que executará a tarefa em um processo correspondente ao contexto de destino. Mesmo se o contexto atual e o contexto de destino corresponderem, você poderá forçar a execução fora de processo de uma tarefa (para fins de isolamento, segurança ou outros) configurando `TaskFactory` para `TaskHostFactory`.  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Parâmetros da tarefa fantasma  
 Como qualquer outro parâmetro de tarefa, `MSBuildRuntime` e `MSBuildArchitecture` podem ser definidos de propriedades de build.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
