---
title: 'Como: usar AsyncPackage para carregar VSPackages em segundo plano | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: gregvanl
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: bcfdf6991c12affc1000ace72b16f97be9de469a
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Como: usar AsyncPackage para carregar VSPackages em segundo plano
Carregar e inicializar um pacote do VS podem resultar em e/s de disco. Se tal e/s acontece no thread da interface do usuário, ele pode levar a problemas de capacidade de resposta. Para resolver isso, o Visual Studio 2015 introduzido a classe < xref:Microsoft.VisualStudio.Shell.AsyncPackage > que permite que o pacote de carregamento em um thread em segundo plano.  
  
## <a name="creating-an-asyncpackage"></a>Criando um AsyncPackage  
 Você pode começar criando um projeto do VSIX (**arquivo / novo / projeto / Visual C# / extensibilidade / projeto VSIX**) e adicionar um VSPackage ao projeto (clique com o botão direito no projeto e **Adicionar/Novo Item / c# item/extensibilidade/Visual Studio pacote**). Você pode criar seus serviços e adicionar os serviços ao seu pacote.  
  
1.  O pacote derivam da < xref:Microsoft.VisualStudio.Shell.AsyncPackage >.  
  
2.  Se você estiver fornecendo serviços cuja consulta pode fazer com que o pacote a ser carregado:  
  
     Para indicar para o Visual Studio que o pacote é seguro para carregamento em segundo plano e para aceitar esse comportamento, < xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute > deve definir **AllowsBackgroundLoading** propriedade como true no construtor de atributo.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Para indicar para o Visual Studio que é seguro criar uma instância de seu serviço em um thread em segundo plano, você deve definir a propriedade < xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A > como true no construtor < xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute >.  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Se você estiver carregando por meio de contextos de interface do usuário, você deve especificar **PackageAutoLoadFlags.BackgroundLoad** para < xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute > ou o valor (0x2) para os sinalizadores são gravados como o valor da entrada de carregamento automático do seu pacote.  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Se você tiver a inicialização assíncrona de trabalho para fazer, você deve substituir < xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A >. Remover o **Initialize** método fornecido pelo modelo do VSIX. (O **Initialize** método **AsyncPackage** está lacrado). Você pode usar qualquer um dos métodos de < xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A > Adicionar serviços assíncronos ao seu pacote.  
  
     Observação: Para chamar **base. InitializeAsync()**, você pode alterar o código-fonte:  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Você deve tomar cuidado para não ter RPCs (chamadas de procedimento remoto) do seu código de inicialização assíncrona (em **InitializeAsync**). Esses podem ocorrer quando você chama < xref:Microsoft.VisualStudio.Shell.Package.GetService%2A > direta ou indiretamente.  Quando as cargas de sincronização são necessárias, o thread de interface do usuário bloqueará usando < xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory >. O modelo de bloqueio padrão desabilita RPCs. Isso significa que, se você tentar usar um RPC de suas tarefas assíncronas, será deadlock se o thread de interface do usuário é aguardando o pacote a ser carregado. A alternativa geral é empacotar seu código para o thread de interface do usuário, se for necessário usar algo como **junções fábrica de tarefas**do < xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A > ou outro mecanismo que não usa um RPC.  Não use **ThreadHelper.Generic.Invoke** ou geralmente bloquear o thread de chamada aguardando para obter o thread de interface do usuário.  
  
     Observação: Você deve evitar usar **GetService** ou **QueryService** no seu **InitializeAsync** método. Se você precisar usá-las, você precisará primeiro alterne para o thread de interface do usuário. A alternativa é usar < xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A > do seu **AsyncPackage** (ao convertê-la para < xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider >.)  
  
 C#: Crie um AsyncPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Converter um VSPackage existente AsyncPackage  
 A maioria do trabalho é o mesmo que criar um novo **AsyncPackage**. Você precisa seguir as etapas 1 a 5 acima. Você também precisa tomar muito cuidado nos seguintes:  
  
1.  Lembre-se de remover o **inicializar** tinha em seu pacote de substituição.  
  
2.  Evitar deadlocks: pode haver oculto RPCs em seu código que agora acontecer em um thread em segundo plano. Você precisa garantir que, se você estiver fazendo uma RPC (por exemplo, **GetService**), você precisa switch (1) para o thread principal ou (2) use a versão assíncrona de API se um existe (por exemplo, **GetServiceAsync**).  
  
3.  Não alterne entre threads com muita frequência. Tente localizar o trabalho que pode ocorrer em um thread em segundo plano. Isso reduz o tempo de carregamento.  
  
## <a name="querying-services-from-asyncpackage"></a>Consultando serviços de AsyncPackage  
 Um **AsyncPackage** podem ou não carregar assincronamente dependendo do chamador. Por exemplo,  
  
-   Se o chamador chamado **GetService** ou **QueryService** (ambas as APIs síncronas) ou  
  
-   Se o chamador chamado **IVsShell::LoadPackage** (ou **IVsShell5::LoadPackageWithContext**) ou  
  
-   O carregamento é disparado por um contexto de interface do usuário, mas você não especificou que o mecanismo de contexto da interface do usuário pode carregar você de forma assíncrona  
  
 em seguida, seu pacote de forma síncrona carregará.  
  
 Observe que o pacote ainda tem uma oportunidade (em sua fase de inicialização assíncrona) para realizar um trabalho do thread de interface do usuário, embora o thread de interface do usuário será bloqueado para a conclusão do trabalho que. Se o chamador usa **IAsyncServiceProvider** a consulta assíncrona para o serviço, em seguida, o carregamento e inicialização serão feitos assincronamente supondo que não bloqueiam imediatamente no objeto tarefa resultante.  
  
 C#: Como consultar o serviço de forma assíncrona:  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```

