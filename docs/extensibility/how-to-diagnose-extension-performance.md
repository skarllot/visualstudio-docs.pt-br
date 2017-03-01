---
title: "Como: diagnosticar o desempenho de extensão | Documentos do Microsoft"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
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
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Medindo o impacto de extensão na inicialização

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Foco no desempenho da extensão no Visual Studio 2017

Com base nos comentários dos clientes, uma das áreas de foco para a versão do Visual Studio 2017 tem sido desempenho de carregamento de inicialização e a solução. Embora, como equipe de plataforma do Visual Studio, temos trabalhado sobre como melhorar o desempenho de carregamento de inicialização e a solução em geral, nossa telemetria sugere extensões instaladas também podem ter um impacto considerável sobre esses cenários.

Para ajudar os usuários a entender esse impacto, adicionamos um novo recurso no Visual Studio para notificar os usuários de extensões lentas. Quando o Visual Studio detecta uma nova extensão que está diminuindo a carga de solução ou de inicialização, os usuários verão uma notificação no IDE apontá-los para a nova caixa de diálogo "Gerenciar Visual Studio Performance". Essa caixa de diálogo também sempre pode ser acessada pelo menu de ajuda para procurar extensões detectadas anteriormente.

![gerenciar o desempenho do Visual Studio](media/manage-performance.png)

Este documento tem como objetivo ajudar os desenvolvedores de extensão descrevendo como o impacto de extensão é calculado e como ele pode ser analisado localmente para testar se uma extensão pode ser mostrada como um impacto sobre a extensão de desempenho.

## <a name="how-extensions-can-impact-startup"></a>Como as extensões podem afetar a inicialização

Uma das maneiras mais comuns para as extensões de impacto no desempenho de inicialização é escolhendo a carga automaticamente em um dos contextos de interface do usuário de inicialização conhecidos como NoSolutionExists ou ShellInitialized. Nesses contextos de interface de usuário obtenham ativados durante a inicialização e todos os pacotes que incluam o atributo "ProvideAutoLoad" em sua definição nesses contextos serão carregados e inicializados neste momento.

Quando medimos o impacto de uma extensão, nos concentramos principalmente em tempo gasto por essas extensões que optar por carregar automaticamente nos contextos acima. Medida tempos seriam incluem, mas não se limitam a:

* Carregamento de assemblies de extensão para pacotes síncronos
* Tempo gasto no construtor da classe de pacote para pacotes síncronos
* Tempo gasto no método Initialize (ou SetSite) de pacote para pacotes síncronos
* Para pacotes assíncronos as operações acima executado no thread em segundo plano e, portanto, serão excluídas de monitoramento
* Tempo gasto em qualquer trabalho assíncrono agendado durante a inicialização do pacote para ser executado no thread principal
* Tempo gasto em manipuladores de eventos, especificamente a ativação do shell inicializado contexto ou a alteração de estado zumbi shell

Adicionamos vários recursos a partir do Visual Studio 2015 ajuda para remover a necessidade de pacotes de carregamento automático, adiar a carga para casos mais específicos em que os usuários seria mais certos usar a extensão ou reduzir o impacto de uma extensão ao carregar automaticamente.

Você pode encontrar mais detalhes sobre esses recursos nos seguintes documentos:

[Regra com base em contextos de interface do usuário](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): um mecanismo de regra com base em mais rico criado em torno de contextos de interface do usuário permitem que você crie os contextos personalizados com base em tipos de projeto, tipos e recursos. Nesses contextos personalizados podem ser usados para carregar um pacote durante cenários mais específicos, como a presença de um projeto com um recurso específico em vez de inicialização; ou permitir [visibilidade seja vinculada a um contexto personalizado de comando](https://msdn.microsoft.com/en-us/library/bb166512.aspx) com base em recursos de projeto ou outros termos disponíveis, eliminando a necessidade de carregar um pacote para registrar um manipulador de consulta de status do comando.

[Suporte assíncrono pacote](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): A nova classe base AsyncPackage no Visual Studio 2015 permite que pacotes sejam carregados em segundo plano assincronamente se carregar o pacote foi solicitado por um atributo de carregamento automático ou uma consulta de serviço assíncrono do Visual Studio. Esse carregamento em segundo plano permite que o IDE permaneça responsivo, enquanto a extensão é inicializada no plano de fundo e cenários essenciais como carga de inicialização e a solução não seria afetados.

[Serviços assíncronos](how-to-provide-an-asynchronous-visual-studio-service.md): com suporte do pacote assíncrono, podemos também adicionou suporte para consultar serviços de forma assíncrona e ser capaz de registrar os serviços assíncronos. Mais importante estamos trabalhando na conversão de serviços do Visual Studio principais para dar suporte à consulta assíncrona, para que a maioria do trabalho em uma consulta assíncrona ocorre em threads em segundo plano. SComponentModel (host do Visual Studio MEF) é um dos serviços principais que agora oferece suporte à consulta assíncrona para permitir extensões dar suporte ao carregamento assíncrono completamente.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reduzir o impacto de auto carregado extensões

Se um pacote ainda precisa ser automaticamente carregado na inicialização, é importante minimizar o trabalho realizado durante a inicialização do pacote para reduzir as chances de que a extensão do impacto sobre a inicialização.

Alguns exemplos que podem causar a inicialização do pacote a ser caro são:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Uso de carregar o pacote síncrona em vez de carregar o pacote assíncrono

Porque síncronos pacotes são carregados no thread principal, por padrão, incentivamos os proprietários de extensão que tenham pacotes automaticamente carregado usa a classe de base do pacote assíncrono, conforme mencionado anteriormente. Alterar um pacote carregado automaticamente para dar suporte a carregamento assíncrono também tornará mais fácil de resolver os problemas abaixo.

### <a name="synchronous-filenetwork-io-requests"></a>Solicitações de e/s síncrona de rede/arquivo

O ideal é qualquer solicitação de e/s de arquivo ou rede síncrona deve ser evitada no thread principal como seu impacto dependerá estado da máquina e pode bloquear por longos períodos de tempo em alguns casos.

Usando o carregamento do pacote assíncrono e APIs de e/s assíncronas deve garantir que a inicialização do pacote não bloqueie o thread principal em tais casos e os usuários podem continuar a interagir com o Visual Studio enquanto as solicitações de e/s acontecem no plano de fundo.

### <a name="early-initialization-of-services-components"></a>Inicialização antecipada de serviços, componentes

Um dos padrões comuns na inicialização do pacote é inicializar serviços usados pelo ou fornecido pelo pacote do método de construtor ou inicializar pacote. Enquanto isso garante que os serviços estão prontos para ser usado, ele também pode adicionar um custo desnecessário para empacotar o carregamento se esses serviços não são usados imediatamente. Em vez disso, esses serviços devem ser inicializados sob demanda para minimizar o trabalho feito na inicialização do pacote.

Para serviços globais fornecidos por um pacote, você pode usar métodos AddService que assume uma função lentamente inicializar o serviço apenas quando solicitado por um componente. Para serviços usados dentro do pacote, você pode utilizar Lazy<T> ou AsyncLazy<T> para garantir que os serviços são inicializados/consultada no primeiro uso.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Medindo o impacto de auto carregado extensões usando PerfView

Embora a análise de código pode ajudar a identificar os caminhos de código que podem causar lentidão na inicialização do pacote, você também pode utilizar o rastreamento usando aplicativos como o PerfView para entender o impacto de um pacote de carga na inicialização do Visual Studio.

PerfView é uma ferramenta de rastreamento ampla do sistema que ajudarão você a compreender os caminhos de acesso em um aplicativo devido a utilização da CPU ou bloqueio de chamadas do sistema. Abaixo está um exemplo rápido sobre como analisar uma extensão de exemplo usando PerfView disponível na [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Código de exemplo:**

Este exemplo é baseado no exemplo de código a seguir, que foi projetado para mostrar algumas causas comuns de atraso de caso:

```c#
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Gravar um rastreamento com PerfView:**

Depois de configurar seu ambiente do Visual Studio com a extensão instalada, você pode gravar um rastreamento de inicialização abrindo PerfView e abrindo a caixa de diálogo coletar no menu "Coletar".

![menu coletar perfview](media/perfview-collect-menu.png)

As opções padrão fornecerá pilhas de chamadas para consumo de CPU, mas já que estamos interessados em tempo de bloqueio, bem, você também deve habilitar pilhas de "Tempo de Thread". Depois que as configurações estão prontas, você pode clicar em "Iniciar coleta" e inicie o Visual Studio depois de gravação é iniciada.

Antes de parar a coleta, convém certificar-se de que o Visual Studio está totalmente inicializado, a janela principal é completamente visível e se sua extensão tiver quaisquer partes da interface do usuário que mostram, automaticamente, eles também são visíveis. Depois que o Visual Studio é completamente carregado e sua extensão é inicializada, você pode interromper a gravação para analisar o rastreamento.

**Analisando um rastreamento com PerfView:**

Após a conclusão da gravação PerfView será automaticamente abrir o rastreamento e opções.

Para os fins deste exemplo, estamos interessados principalmente no modo de exibição "Pilhas de tempo do Thread" que pode ser encontrado em "Advanced Group". Essa exibição mostrará o tempo total gasto em um thread por um método incluindo o tempo de CPU e tempo bloqueado, como e/s de disco ou aguardando identificadores.

 ![pilhas de tempo do thread](media/perfview-thread-time-stacks.png)

 Ao abrir a exibição "Thread pilhas de tempo", você deve escolher o processo de "devenv" para iniciar a análise.

PerfView tem orientação detalhada sobre como ler thread pilhas de tempo em seu próprio menu de ajuda para uma análise mais detalhada. Para fins deste exemplo, queremos filtrar ainda mais esta exibição só incluindo pilhas com nossa thread de inicialização e o nome de módulo pacotes.

1. Defina "GroupPats" como texto vazio para remover qualquer agrupamento adicionado por padrão.
2. Defina "IncPats" para incluir parte do nome do assembly e inicialização de Thread além de filtro de processo existente. Nesse caso, ele deve ser "devenv; Thread de inicialização. MakeVsSlowExtension".

Agora a exibição mostrará apenas custo associado com os assemblies relacionados a extensão. Nesse modo, sempre listado na coluna "Inc." (Inclusive custo) do thread de inicialização está relacionado à nossa extensão filtrado e irá afetar a inicialização.

No exemplo acima algumas interessante chamada pilhas seria:

1. E/s usando a classe System.IO: enquanto inclusive custo desses quadros não pode ser muito caro no rastreamento, eles são uma causa potencial de um problema já que a velocidade de e/s de arquivo irá variar de máquina para máquina.

  ![quadros de e/s do sistema](media/perfview-system-io-frames.png)

2. Bloqueio de chamadas, aguardando outro trabalho assíncrono: nesse caso tempo inclusive representa a hora em que o thread principal seja bloqueado na conclusão do trabalho assíncrono.

  ![quadros de chamada de bloqueio](media/perfview-blocking-call-frames.png)

Um dos outros modos de exibição no rastreamento que serão úteis para determinar o impacto será as pilhas de carga"imagem". Você pode aplicar os mesmo filtros conforme aplicadas à exibição "Thread pilhas de tempo" e descobrir todos os assemblies carregados devido o código executado por seu pacote carregado automaticamente.

É importante minimizar o número de assemblies carregados dentro de uma rotina de inicialização do pacote como cada assembly adicional envolve a e/s de disco extra que pode causar lentidão na inicialização consideravelmente em computadores mais lentos.

## <a name="summary"></a>Resumo

Inicialização do Visual Studio tem sido uma das áreas que sempre Obtenha comentários sobre. Nosso objetivo, conforme mencionado anteriormente é para todos os usuários tenham uma inicialização consistente a experiência independentemente de componentes e extensões de que terem instalado e gostaríamos de trabalhar com os proprietários de extensão para ajudá-los nos ajudar a alcançar esse objetivo. A orientação acima deve ser úteis em entender o impacto extensões na inicialização e pode evitar a necessidade de automático de carga ou carregá-lo de forma assíncrona, para minimizar o impacto na produtividade do usuário.
