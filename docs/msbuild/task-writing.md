---
title: "Escrevendo tarefas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, criando tarefas"
  - "MSBuild, gravando tarefas"
  - "tarefas, criando para MSBuild"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Escrevendo tarefas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tarefas fornecem o código que executa durante o processo de compilação.  As tarefas estão contidas nos destinos.  Uma biblioteca de tarefas típicas está incluída no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], e você também pode criar suas próprias tarefas.  Para obter mais informações sobre a biblioteca de tarefas que estão incluídos no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consulte [Referência de tarefas](../msbuild/msbuild-task-reference.md).  
  
## Tarefas  
 Exemplos de tarefas  [Copy](../msbuild/copy-task.md), que copia um ou mais arquivos,  [MakeDir](../msbuild/makedir-task.md), que cria um diretório, e  [Csc](../msbuild/csc-task.md), que compila [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] arquivos de código de origem.  Cada tarefa é implementada como um.NET classe que implementa o <xref:Microsoft.Build.Framework.ITask> interface, que é definido no assembly Microsoft.Build.Framework.dll.  
  
 Há duas abordagens que você pode usar durante a implementação de uma tarefa:  
  
-   Implementar a <xref:Microsoft.Build.Framework.ITask> interface diretamente.  
  
-   Derivar a classe da classe auxiliar, <xref:Microsoft.Build.Utilities.Task>, que é definido no assembly Microsoft.Build.Utilities.dll.  Tarefa implementa ITask e fornece implementações padrão de alguns membros ITask.  Além disso, o log é mais fácil.  
  
 Em ambos os casos, você deve adicionar à sua classe um método chamado `Execute`, que é o método que é chamado quando a tarefa é executada.  Esse método sem parâmetros e retorna um `Boolean` valor: `true` se a tarefa foi bem\-sucedida ou `false` se ele falhar.  O exemplo a seguir mostra uma tarefa que não executa nenhuma ação e retorna `true`.  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 O arquivo de projeto a seguir executa essa tarefa:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Quando as tarefas executadas, elas também podem receber entradas do arquivo de projeto se você criar.NET propriedades na classe task.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]define essas propriedades imediatamente antes de chamar a tarefa `Execute` método.  Para criar uma propriedade de cadeia de caracteres, use o código da tarefa como:  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 O seguinte arquivo será executado de projeto desta tarefa e conjuntos de `MyProperty` para o valor fornecido:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## Registrando tarefas  
 Se for um projeto para executar uma tarefa, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve saber como localizar o assembly que contém a classe de tarefa.  Tarefas são registradas usando o [Elemento UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
 O [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Microsoft.Common.Tasks é um arquivo de projeto que contém uma lista de `UsingTask` elementos que registram todas as tarefas que são fornecidas com [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Este arquivo é incluído automaticamente na criação de cada projeto.  Se uma tarefa que está registrada no Microsoft.Common.Tasks também é registrada no arquivo de projeto atual, o arquivo de projeto atual tem prioridade; ou seja, você pode substituir uma tarefa padrão com sua própria tarefa que tem o mesmo nome.  
  
> [!TIP]
>  Você pode ver uma lista das tarefas que são fornecidos com [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] , exibindo o conteúdo de Microsoft.Common.Tasks.  
  
## Geração de eventos a partir de uma tarefa  
 Se sua tarefa deriva o <xref:Microsoft.Build.Utilities.Task> classe auxiliar, você pode usar qualquer um dos seguintes métodos auxiliares na <xref:Microsoft.Build.Utilities.Task> classe para gerar eventos que serão capturados e exibidos por qualquer loggers registrados:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Se sua tarefa implementa <xref:Microsoft.Build.Framework.ITask> diretamente, você ainda pode elevar eventos desse tipo, mas você deve usar a interface de IBuildEngine.  O exemplo a seguir mostra uma tarefa que implementa ITask e gera um evento personalizado:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## Exigir que os parâmetros da tarefa a ser definido  
 Para que qualquer arquivo de projeto que executa a tarefa deve definir valores para essas propriedades ou a construção falhar, você pode marcar determinadas propriedades de tarefa como "obrigatórias".  Aplicar o `[Required]` de atributo para o.NET propriedade na sua tarefa, da seguinte maneira:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 O `[Required]` atributo é definido por <xref:Microsoft.Build.Framework.RequiredAttribute> na <xref:Microsoft.Build.Framework> espaço para nome.  
  
## Exemplo  
  
### Descrição  
 Seguir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe demonstra uma tarefa de derivar o <xref:Microsoft.Build.Utilities.Task> classe auxiliar.  Esta tarefa retorna `true`, indicando que ele teve êxito.  
  
### Código  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Exemplo  
  
### Descrição  
 Seguir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe demonstra uma tarefa de implementar a <xref:Microsoft.Build.Framework.ITask> interface.  Esta tarefa retorna `true`, indicando que ele teve êxito.  
  
### Código  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Exemplo  
  
### Descrição  
 Isso [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] classe demonstra uma tarefa que deriva do <xref:Microsoft.Build.Utilities.Task> classe auxiliar.  Ele tem uma propriedade de seqüência de caracteres necessários e gerará um evento que é exibido por todos os loggers registrados.  
  
### Código  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## Exemplo  
  
### Descrição  
 O exemplo a seguir mostra um arquivo de projeto, a tarefa de exemplo anterior, SimpleTask3 é chamada.  
  
### Código  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)