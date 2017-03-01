---
title: 'Como: usar AsyncPackage para carregar os VSPackages em segundo plano | Documentos do Microsoft'
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
ms.sourcegitcommit: b6c1267ddbebc3ed1feb3aa2c7c818e2b0ca9631
ms.openlocfilehash: c13ffe48ab3bf971d15c361d2423a0bb3f59fe78
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Como: usar AsyncPackage para carregar os VSPackages em segundo plano
Carregar e inicializar um VS package podem resultar em e/s de disco. Se tal e/s acontece no thread da interface do usuário, ele pode levar a problemas de capacidade de resposta. Para resolver isso, o Visual Studio 2015 introduziu o <xref:Microsoft.VisualStudio.Shell.AsyncPackage>classe que permite o carregamento do pacote em um thread em segundo plano.</xref:Microsoft.VisualStudio.Shell.AsyncPackage>  
  
## <a name="creating-an-asyncpackage"></a>Criando um AsyncPackage  
 Você pode começar criando um projeto do VSIX (**arquivo / novo / projeto / Visual c# / extensibilidade / projeto do VSIX**) e adicionando um VSPackage no projeto (clique com o botão direito no projeto e **Adicionar/Novo Item / c# item/extensibilidade/Visual Studio Package**). Em seguida, você pode criar seus serviços e adicionar esses serviços ao seu pacote.  
  
1.  Derivar o pacote de <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.</xref:Microsoft.VisualStudio.Shell.AsyncPackage>  
  
2.  Se você estiver fornecendo serviços cuja consulta pode fazer com que o pacote a ser carregado:  
  
     Para indicar ao Visual Studio que o pacote é seguro para carregamento em segundo plano e aceitar esse comportamento, o <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>deve definir **AllowsBackgroundLoading** propriedade como true no construtor de atributo.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Para indicar ao Visual Studio que é seguro instanciar o serviço em um thread em segundo plano, você deve definir o <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A>propriedade como true no <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>construtor.</xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A>  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Se você estiver carregando através de contextos de interface do usuário, você deve especificar **PackageAutoLoadFlags.BackgroundLoad** para o <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>ou o valor (0x2) para os sinalizadores escrito como o valor da entrada de carga automático do seu pacote.</xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Se você tiver a inicialização assíncrona de trabalho para fazer, você deve substituir <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>.</xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A> Remover o **Initialize ()** método fornecido pelo modelo do VSIX. (O **Initialize ()** método **AsyncPackage** está lacrado). Você pode usar qualquer um dos <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>métodos para adicionar serviços assíncronos ao seu pacote.</xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A>  
  
     Observação: Para chamar **base. InitializeAsync()**, você pode alterar seu código-fonte para:  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Você deve tomar cuidado para não ter RPCs (chamada de procedimento remover) no seu código de inicialização assíncrona (em **InitializeAsync**). Eles podem ocorrer quando você chamar <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>direta ou indiretamente.</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  Quando forem necessárias cargas de sincronização, o thread de interface do usuário bloqueará o uso <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> O modelo de bloqueio padrão desabilita RPCs. Isso significa que, se você tentar usar uma RPC de suas tarefas assíncronas, será bloqueada se o thread de interface do usuário é esperar do seu pacote para carregar. A alternativa geral é empacotar o seu código no thread da interface do usuário se for necessário usar algo como **junções Factory tarefa**do <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>ou algum outro mecanismo que não usa um RPC.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>  Não use **ThreadHelper.Generic.Invoke** ou geralmente bloquear o thread de chamada aguardando para obter o thread da interface do usuário.  
  
     Observação: Você deve evitar usar **GetService** ou **QueryService** em seu **InitializeAsync** método. Se você precisar usá-los, você precisará alternar para o thread de interface do usuário primeiro. A alternativa é usar <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A>de seu **AsyncPackage** (convertendo para <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)</xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider> </xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A>  
  
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
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Converter um VSPackage existente em AsyncPackage  
 A maioria do trabalho é o mesmo que criar um novo **AsyncPackage**. Você precisa seguir as etapas 1 a 5 acima. Você também precisa tomar cuidado extra no seguinte:  
  
1.  Lembre-se de remover o **inicializar** substituição tinha no pacote.  
  
2.  Evitar deadlocks: pode haver oculto RPCs em seu código que agora acontecer em um thread em segundo plano. Você precisa garantir que, se você estiver fazendo uma RPC (por exemplo, **GetService**), você precisa switch (1) para o thread principal ou (2) use a versão assíncrona do API se um existe (por exemplo, **GetServiceAsync**).  
  
3.  Alterna entre threads com muita frequência. Tente localizar o trabalho que pode acontecer em um thread em segundo plano. Isso reduz o tempo de carregamento.  
  
## <a name="querying-services-from-asyncpackage"></a>Consultando serviços de AsyncPackage  
 Um **AsyncPackage** podem ou não carregar assíncrona dependendo do chamador. Por exemplo,  
  
-   Se o chamador chamado **GetService** ou **QueryService** (ambas as APIs síncronas) ou  
  
-   Se o chamador chamado **IVsShell::LoadPackage** (ou **IVsShell5::LoadPackageWithContext**) ou  
  
-   O carregamento é disparado por um contexto de interface do usuário, mas você não especificou que o mecanismo de contexto da interface do usuário pode carregar você de forma assíncrona  
  
 em seguida, o pacote carregará sincronicamente.  
  
 Observe que o pacote ainda tem uma oportunidade (em sua fase de inicialização assíncrona) para trabalhar fora do thread da interface do usuário, embora o thread da interface do usuário será bloqueado para a conclusão do trabalho. Se o chamador usa **IAsyncServiceProvider** a consulta assíncrona para o serviço, em seguida, seu carregamento e inicialização serão feitos assincronamente supondo que não bloquear imediatamente no objeto da tarefa resultante.  
  
 C#: Como consultar o serviço de forma assíncrona:  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
