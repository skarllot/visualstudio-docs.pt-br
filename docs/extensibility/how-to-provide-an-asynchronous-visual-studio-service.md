---
title: "Como: fornecer um serviço assíncrono do Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4948fee531ff0887dc4d0fe010aacbaf17b941b4
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Como: fornecer um serviço assíncrono do Visual Studio
Se você quiser obter um serviço sem bloquear o thread da interface do usuário, você deve criar um serviço assíncrono e carregue o pacote em um thread em segundo plano. Para essa finalidade, você pode usar um <xref:Microsoft.VisualStudio.Shell.AsyncPackage>em vez de um <xref:Microsoft.VisualStudio.Shell.Package>e adicione o serviço com os métodos assíncronos especial do pacote assíncrono</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.AsyncPackage>  
  
 Para obter informações sobre o fornecimento de serviços síncronos do Visual Studio, consulte [como: fornecer um serviço](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Implementando um serviço assíncrono  
  
1.  Criar um projeto do VSIX (**arquivo / novo / projeto / Visual c# / Extensiblity / projeto do VSIX**). Nomeie o projeto **TestAsync**.  
  
2.  Adicione um VSPackage no projeto. Selecione o nó do projeto no **Solution Explorer** e clique em **adicionar / novo item / itens do Visual c# / extensibilidade / pacote do Visual Studio**. Nomeie esse arquivo **TestAsyncPackage.cs**.  
  
3.  No TestAsyncPackage.cs, altere o pacote para herdar de AsyncPackage em vez de pacote:  
  
    ```c#  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Para implementar um serviço, você precisa criar três tipos:  
  
    -   Uma interface que descreve o serviço. Muitas dessas interfaces estiverem vazias, ou seja, eles têm não métodos.  
  
    -   Uma interface que descreve a interface de serviço. Essa interface inclui os métodos a serem implementados.  
  
    -   Uma classe que implementa o serviço e a interface de serviço.  
  
5.  O exemplo a seguir mostra uma implementação muito básica dos três tipos. O construtor da classe de serviço deve definir o provedor de serviços. Neste exemplo, apenas adicionaremos o serviço para o arquivo de código do pacote.  
  
6.  Adicione as seguintes instruções using ao arquivo de pacote:  
  
    ```c#  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Aqui está a implementação de serviço assíncrono. Observe que você precisa definir o provedor de serviço assíncrono em vez do provedor de serviço síncronas no construtor:  
  
    ```  
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;  
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)  
        {  
            serviceProvider = provider;  
        }  
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
        public TaskAwaiter GetAwaiter()  
        {  
            return new TaskAwaiter();  
        }  
    }  
    public interface STextWriterService  
    {  
    }  
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
        TaskAwaiter GetAwaiter();  
    }  
    ```  
  
## <a name="registering-a-service"></a>Registrar um serviço  
 Para registrar um serviço, adicione a <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>para o pacote que fornece o serviço.</xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Há duas diferenças de registrar um serviço síncrono:  
  
-   Se você realiza o carregamento automático do pacote, você deve adicionar o <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>valor BackgroundLoad ao atributo.</xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> Para obter mais informações sobre os VSPackages realiza o carregamento automático, consulte [VSPackages Carregando](../extensibility/loading-vspackages.md).  
  
-   Você deve adicionar o **AllowsBackgroundLoading = true** campo para <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Para obter mais informações sobre o PackageRegistrationAttribute, consulte [Registrando e Cancelando o registro VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Aqui está um exemplo de um AsyncPackage com um registro de serviço assíncrono:  
  
```c#  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Adicionando um serviço  
  
1.  No TestAsyncPackage.cs, remova o `Initialize()` método e substituir o `InitializeAsync()` método. Adicionar o serviço e adicionar um método de retorno de chamada para criar os serviços. Aqui está um exemplo do inicializador do assíncrono adicionando um serviço:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Adicione uma referência ao Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implemente o método de retorno de chamada como um método assíncrono que cria e retorna o serviço.  
  
    ```c#  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## <a name="using-a-service"></a>Usando um serviço  
 Agora você pode obter o serviço e usar seus métodos.  
  
1.  Vamos mostrar isso no inicializador, mas você pode obter o serviço em qualquer lugar que deseja usar o serviço.  
  
    ```c#  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Não se esqueça de alterar * \<userpath >* para um nome de arquivo e caminho que faça sentido em seu computador!  
  
2.  Compile e execute o código. Quando for exibida a instância experimental do Visual Studio, abra uma solução. Isso faz com que o AsyncPackage carregar. Quando o inicializador é executado, você deve encontrar um arquivo no local especificado.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Usando um serviço assíncrono em um manipulador de comandos  
 Aqui está um exemplo de como usar um serviço assíncrono em um comando de menu. Você pode usar o procedimento mostrado aqui para usar o serviço de outros métodos não assíncronas.  
  
1.  Adicione um comando de menu ao seu projeto. (No **Solution Explorer**, selecione o nó do projeto, clique com botão direito e selecione **Adicionar / Novo Item / extensibilidade personalizada de comando /**.) Nomeie o arquivo de comando **TestAsyncCommand.cs.**  
  
2.  O modelo de comando personalizado adiciona novamente o `Initialize()` método ao arquivo TestAsyncPackage.cs para inicializar o comando. No método Initialize (), copie a linha que inicializa o comando. Ele deve ser assim:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Mova essa linha para o `InitializeAsync()` método no arquivo AsyncPackageForService.cs. Como se trata a inicialização assíncrona, você deve alternar para o thread principal antes de inicializar o comando usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Agora, ele deve ser assim:  
  
    ```c#  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);    
  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync((<userpath>, "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
3.  Excluir o `Initialize()` método.  
  
4.  No arquivo TestAsyncCommand.cs, localize o `MenuItemCallback()` método. Exclua o corpo do método.  
  
5.  Adicionar um uso a instrução:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Adicionar um método assíncrono chamado `GetAsyncService()`, que obtém o serviço e usa seus métodos:  
  
    ```c#  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Chamar esse método a partir de `MenuItemCallback()` método:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Compile a solução e inicie a depuração. Quando for exibida a instância experimental do Visual Studio, vá para o **ferramentas** menu e procure o **TestAsyncCommand invocar** item de menu. Quando você clica nele, o TextWriterService grava o arquivo especificado. (Você não precisa abrir uma solução, como invocar o comando também faz com que o pacote a ser carregado.)  
  
## <a name="see-also"></a>Consulte também  
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)
