---
title: "Gravação de Tarefa| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
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
ms.openlocfilehash: 2ebc4bacb2f90bc0f15e2178126e383e8c43e2f1
ms.lasthandoff: 02/22/2017

---
# <a name="task-writing"></a>Escrevendo tarefas
Tarefas fornecem o código que é executado durante o processo de build. Tarefas estão contidas nos destinos. Uma biblioteca de tarefas típicas está incluída no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] e você também pode criar suas próprias tarefas. Para obter mais informações sobre a biblioteca de tarefas que estão incluídos no [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], consulte [referência à tarefa](../msbuild/msbuild-task-reference.md).  
  
## <a name="tasks"></a>Tarefas  
 Exemplos de tarefas incluem [Copiar](../msbuild/copy-task.md), que copia um ou mais arquivos, [MakeDir](../msbuild/makedir-task.md), que cria um diretório e [Csc](../msbuild/csc-task.md), que compila arquivos de código-fonte [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Cada tarefa é implementada como uma classe .NET que implementa a interface <xref:Microsoft.Build.Framework.ITask>, que é definida no assembly Microsoft.Build.Framework.dll.  
  
 Há duas abordagens que você pode usar ao implementar uma tarefa:  
  
-   Implementar a interface <xref:Microsoft.Build.Framework.ITask> diretamente.  
  
-   Deriva sua classe da classe auxiliar, <xref:Microsoft.Build.Utilities.Task>, que é definida no assembly Microsoft.Build.Utilities.dll. Tarefa implementa ITask e fornece implementações padrão de alguns membros do ITask. Além disso, o registro em log é mais fácil.  
  
 Em ambos os casos, você deve adicionar à sua classe um método chamado `Execute`, que é o método que é chamado quando a tarefa é executada. Esse método não usa nenhum parâmetro e retorna um `Boolean` valor: `true` se a tarefa foi bem-sucedida ou `false` se falhou. O exemplo a seguir mostra uma tarefa que não executa nenhuma ação e retorna `true`.  
  
```cs
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
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Quando executar tarefas, elas também poderá receber entradas do arquivo de projeto se você criar propriedades .NET na classe task. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] define essas propriedades imediatamente antes de chamar o método de tarefa `Execute`. Para criar uma propriedade de cadeia de caracteres, use o código da tarefa como:  
  
```cs
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
  
 O seguinte arquivo de projeto executa essa tarefa e define `MyProperty` como o valor especificado:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## <a name="registering-tasks"></a>Registrando tarefas  
 Se um projeto for executar uma tarefa, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deverá saber como localizar o assembly que contém a classe de tarefa. Tarefas são registradas usando o [elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 O arquivo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Microsoft.Common.Tasks é um arquivo de projeto que contém uma lista de elementos `UsingTask` que registra todas as tarefas que são fornecidas com [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Esse arquivo é incluído automaticamente na criação de cada projeto. Se uma tarefa que está registrada no Microsoft.Common.Tasks também é registrada no arquivo de projeto atual, o arquivo de projeto atual tem precedência; ou seja, você pode substituir uma tarefa padrão com sua própria tarefa que tem o mesmo nome.  
  
> [!TIP]
>  Você pode ver uma lista de tarefas que são fornecidos com [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] exibindo o conteúdo de Microsoft.Common.Tasks.  
  
## <a name="raising-events-from-a-task"></a>Gerando eventos de uma tarefa  
 Se a tarefa deriva a classe auxiliar <xref:Microsoft.Build.Utilities.Task>, você pode usar qualquer um dos seguintes métodos auxiliares na classe <xref:Microsoft.Build.Utilities.Task> para gerar eventos que serão capturados e exibidos por quaisquer agentes registrados:  
  
```cs
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Se a tarefa implementa <xref:Microsoft.Build.Framework.ITask> diretamente, você ainda pode gerar eventos, mas você deve usar a interface IBuildEngine. O exemplo a seguir mostra uma tarefa que implementa ITask e gera um evento personalizado:  
  
```cs
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
  
## <a name="requiring-task-parameters-to-be-set"></a>Parâmetros de tarefa necessários a serem definidos  
 Você pode marcar determinadas propriedades de tarefa como "necessárias" para que qualquer arquivo de projeto que executa a tarefa deve definir valores para essas propriedades ou o build falhará. Aplicar o atributo `[Required]` à propriedade .NET em sua tarefa da seguinte maneira:  
  
```cs
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 O atributo `[Required]` é definido por <xref:Microsoft.Build.Framework.RequiredAttribute> no namespace <xref:Microsoft.Build.Framework>.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Essa classe a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] seguir demonstra uma tarefa derivando da classe auxiliar <xref:Microsoft.Build.Utilities.Task>. Esta tarefa retorna `true`, indicando que foi bem-sucedida.  
  
### <a name="code"></a>Código  
  
```cs
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
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Essa classe a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] seguir demonstra uma tarefa implementado a interface <xref:Microsoft.Build.Framework.ITask>. Esta tarefa retorna `true`, indicando que foi bem-sucedida.  
  
### <a name="code"></a>Código  
  
```cs
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
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Essa classe a [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] seguir demonstra uma tarefa derivando da classe auxiliar <xref:Microsoft.Build.Utilities.Task> helper class. Tem uma propriedade de cadeia de caracteres obrigatória e gera um evento que é exibido por todos os agentes registrados.  
  
### <a name="code"></a>Código  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir mostra um arquivo de projeto invocando a tarefa de exemplo anterior, SimpleTask3.  
  
### <a name="code"></a>Código  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
