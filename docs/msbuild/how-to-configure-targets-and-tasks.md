---
title: "Como configurar destinos e tarefas | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Como configurar destinos e tarefas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tarefas do MSBuild selecionadas podem ser definidas para ser executado no ambiente de destino, independentemente do ambiente do computador de desenvolvimento.  Por exemplo, quando você usa um computador de 64 bits para criar um aplicativo essa arquitetura de 32 bits de destinos, as tarefas selecionadas são executadas em um processo de 32 bits.  
  
> [!NOTE]
>  Se uma tarefa de compilação estiver escrita em um.NET de linguagem, como, por exemplo, Visual C\# ou Visual Basic, e é não usar recursos nativos ou ferramentas, em seguida, ele será executado em qualquer contexto de destino sem adaptação.  
  
## Atributos UsingTask e os parâmetros da tarefa  
 O seguinte `UsingTask` atributos afetam todas as operações de uma tarefa em um processo de compilação específica:  
  
-   O `Runtime` atributo, se presente, define a versão de tempo de execução \(CLR\) de idioma comum e pode levar a qualquer um destes valores: `CLR2`, `CLR4`, `CurrentRuntime`, ou `*` \(qualquer tempo de execução\).  
  
-   O `Architecture` atributo, se presente, define a plataforma e o número de bits e pode levar a qualquer um destes valores: `x86`, `x64`, `CurrentArchitecture`, ou `*` \(qualquer arquitetura\).  
  
-   O `TaskFactory` atributo, se presente, define a fábrica de tarefa que cria e executa a instância de tarefa e usa apenas o valor `TaskHostFactory`.  Para obter mais informações, consulte a seção tarefas fábricas mais adiante neste documento.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Você também pode usar o `MSBuildRuntime` e `MSBuildArchitecture` parâmetros para definir o contexto de destino de uma tarefa individual.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Antes de MSBuild é executado em uma tarefa, ele procura uma correspondência `UsingTask` que tem o mesmo contexto de destino.  Os parâmetros especificados na `UsingTask` mas não na tarefa correspondente são considerados a ser correspondido.  Parâmetros especificados na tarefa mas não no correspondente `UsingTask` também são considerados a ser correspondido.  Se os valores de parâmetro não forem especificados em ambos os `UsingTask` ou a tarefa, os valores padrão para `*` \(qualquer parâmetro\).  
  
> [!WARNING]
>  Se mais de um `UsingTask` existe e todos têm correspondência `TaskName`, `Runtime`, e `Architecture` atributos, o último elemento a ser avaliada substitui os outros.  
  
 Se os parâmetros são definidos na tarefa, o MSBuild tentará encontrar uma `UsingTask` que corresponde a esses parâmetros ou, pelo menos, não está em conflito com eles.  Mais de um `UsingTask` pode especificar o contexto de destino da mesma tarefa.  Por exemplo, uma tarefa que tenha os executáveis diferentes para ambientes de destino diferente pode ser semelhante a esta:  
  
```  
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
  
## Fábricas de tarefa  
 Antes de executar uma tarefa, MSBuild verifica se ele é designado para ser executado no contexto atual do software.  Se a tarefa tão designada, o MSBuild passá\-lo para o AssemblyTaskFactory, o qual ele é executado no processo atual; Caso contrário, o MSBuild passa a tarefa para o TaskHostFactory, que executa a tarefa em um processo que coincide com o contexto de destino.  Mesmo que corresponde ao contexto atual e o contexto de destino, você pode forçar uma tarefa para execução fora de processo \(para isolamento, segurança ou outros motivos\), definindo `TaskFactory` para `TaskHostFactory`.  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## Parâmetros da tarefa fantasma  
 Como qualquer outro parâmetro da tarefa, `MSBuildRuntime` e `MSBuildArchitecture` pode ser definido de propriedades de compilação.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Ao contrário de outros parâmetros de tarefa, `MSBuildRuntime` e `MSBuildArchitecture` não são aparentes à tarefa propriamente dito.  Para escrever uma tarefa que está ciente do contexto no qual ele é executado, você deve testar o contexto chamando o.NET Framework ou use as propriedades de compilação para passar as informações de contexto por meio de outros parâmetros da tarefa.  
  
> [!NOTE]
>  `UsingTask`é possível definir atributos das propriedades do conjunto de ferramentas e ambiente.  
  
 O `MSBuildRuntime` e `MSBuildArchitecture` parâmetros fornecem a maneira mais flexível para definir o contexto de destino, mas também o mais limitado no escopo.  Por um lado, porque elas são definidas na própria instância de tarefa e não são avaliadas até que a tarefa está prestes a executar, eles podem derivar seus valores do escopo completo das propriedades disponíveis no tempo de compilação e tempo de avaliação.  Por outro lado, esses parâmetros se aplicam somente a uma instância particular de uma tarefa em um destino específico.  
  
> [!NOTE]
>  Parâmetros da tarefa são avaliados no contexto do nó pai, e não no contexto de host de tarefas.Variáveis de ambiente que são dependentes em tempo de execução ou de arquitetura \(como, por exemplo, a localização de arquivos de programa\) irá avaliar o valor que corresponde ao nó pai.  No entanto, se a mesma variável de ambiente é lidos diretamente pela tarefa, ele corretamente será avaliado no contexto do host de tarefas.  
  
## Consulte também  
 [Configurando destinos e tarefas](../msbuild/configuring-targets-and-tasks.md)