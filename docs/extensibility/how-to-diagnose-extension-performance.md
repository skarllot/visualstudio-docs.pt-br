---
title: "Como: diagnosticar o desempenho de extensão | Microsoft Docs"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b78a02b9d780b9556cbbf42fce04b1da06e22833
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Medir o impacto de extensão na inicialização

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Foque no desempenho de extensão no Visual Studio de 2017

Com base nos comentários dos clientes, uma das áreas de foco para a versão do Visual Studio de 2017 foi desempenho de carregamento de inicialização e a solução. Embora, como a equipe de plataforma do Visual Studio, trabalhamos na melhoria do desempenho de carregamento de inicialização e a solução em geral, nosso telemetria sugere extensões instaladas também podem ter um impacto considerável sobre esses cenários.

Para ajudar os usuários a compreender esse impacto, adicionamos um novo recurso no Visual Studio para notificar os usuários de extensões lenta. Quando o Visual Studio detecta uma nova extensão está diminuindo a carga de solução ou de inicialização, os usuários verão uma notificação no IDE apontá-los para a nova caixa de diálogo "Gerenciar Visual Studio Performance". Essa caixa de diálogo também sempre pode ser acessada pelo menu de ajuda para procurar extensões detectadas anteriormente.

![gerenciar o desempenho do Visual Studio](media/manage-performance.png)

Este documento visa ajudar os desenvolvedores de extensão descrevendo como o impacto de extensão é calculado e como ele pode ser analisado localmente para testar se uma extensão pode ser mostrada como um impacto de extensão de desempenho.

## <a name="how-extensions-can-impact-startup"></a>Como as extensões podem afetar a inicialização

Uma das maneiras mais comuns para as extensões de impacto no desempenho de inicialização é escolhendo a carga automaticamente em um dos contextos de interface do usuário de inicialização conhecidos como NoSolutionExists ou ShellInitialized. Nesses contextos de interface de usuário obtenham ativados durante a inicialização e todos os pacotes que incluem o atributo "ProvideAutoLoad" em sua definição nesses contextos serão carregados e inicializados neste momento.

Quando medimos o impacto de uma extensão, nosso foco principalmente no tempo gasto por essas extensões que escolher para a carga automaticamente em contextos acima. Medida vezes seriam incluem, mas não se limitam a:

* Carregamento de assemblies de extensão para pacotes síncronos
* Tempo gasto no construtor da classe de pacote para pacotes síncronos
* Tempo gasto no método Initialize (ou SetSite) de pacote para pacotes síncronos
* Para pacotes assíncronos as operações acima executado em um thread em segundo plano e, portanto, serão excluídas de monitoramento
* Tempo gasto em qualquer trabalho assíncrono agendado durante a inicialização do pacote para execução no thread principal
* Tempo gasto em manipuladores de eventos, a ativação do contexto de shell inicializado especificamente ou a alteração de estado de zumbi shell
* A partir da atualização 3 do Visual Studio de 2017, também começaremos monitorando o tempo gasto em chamadas ociosas antes da inicialização do shell. Operações longas em manipuladores ociosos também fazer com que o IDE não responder e contribuem para o tempo de inicialização percebido pelo usuário.

Adicionamos vários recursos, a partir do Visual Studio 2015 para ajudar com a remoção a necessidade de pacotes para carregar automaticamente, adiar a carga mais específico casos em que os usuários seria mais determinados usar a extensão ou reduzir o impacto de uma extensão ao carregar automaticamente.

Você pode encontrar mais detalhes sobre esses recursos nos seguintes documentos:

[Regra com base em contextos de interface do usuário](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): um mecanismo com base em regra avançado criado em torno de contextos de interface de usuário permitem que você crie contextos personalizados com base em tipos de projeto, tipos e recursos. Nesses contextos personalizados podem ser usados para carregar um pacote durante cenários mais específicos, como a presença de um projeto com um recurso específico em vez de inicialização; ou permitir [comando visibilidade seja vinculado a um contexto personalizado](https://msdn.microsoft.com/en-us/library/bb166512.aspx) com base em recursos de projeto ou outros termos disponíveis, eliminando a necessidade de carregar um pacote para registrar um manipulador de consulta de status do comando.

[Suporte de pacote assíncrono](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): A nova classe de base AsyncPackage no Visual Studio 2015 permite que os pacotes do Visual Studio ser carregado no plano de fundo assincronamente se carregar o pacote foi solicitado por um atributo de carregamento automático ou uma consulta de serviço assíncrona . Esse carregamento em segundo plano permite que o IDE permaneça responsivo enquanto a extensão é inicializada no plano de fundo e cenários críticos como carga de inicialização e a solução não seria afetados.

[Serviços assíncronos](how-to-provide-an-asynchronous-visual-studio-service.md): com suporte de pacote assíncrono também adicionamos suporte consultando os serviços de forma assíncrona e conseguir registrar serviços assíncronos. É mais importante estamos trabalhando sobre a conversão de serviços do Visual Studio principais para dar suporte à consulta assíncrona para que a maioria do trabalho em uma consulta assíncrona ocorre em threads em segundo plano. SComponentModel (host de MEF do Visual Studio) é um dos serviços principais que agora oferece suporte à consulta assíncrona para permitir extensões dar suporte ao carregamento assíncrono completamente.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reduzir o impacto de auto carregado extensões

Se um pacote deve ser automaticamente carregado na inicialização, é importante minimizar o trabalho feito durante a inicialização do pacote para reduzir as chances de que a extensão de afetar a inicialização.

Alguns exemplos que podem causar a inicialização do pacote a ser caro são:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Uso de carregar o pacote síncrona em vez de carregar o pacote assíncrona

Como síncronos pacotes são carregados no thread principal por padrão, recomendamos que proprietários de extensão que tenham pacotes automaticamente carregado usa a classe de base do pacote assíncrono, conforme mencionado anteriormente. Alterar um pacote carregado automaticamente para dar suporte a carregamento assíncrono também tornará mais fácil de resolver os problemas abaixo.

### <a name="synchronous-filenetwork-io-requests"></a>Solicitações de e/s de arquivo síncrono/rede

O ideal é qualquer solicitação síncrona de e/s de arquivo ou de rede deve ser evitada no thread principal como seu impacto depende o estado da máquina e pode bloquear por longos períodos de tempo, em alguns casos.

Usar o carregamento do pacote assíncrona e APIs de e/s assíncronas deve garantir que a inicialização do pacote não bloqueia o thread principal em tais casos, e os usuários podem continuar a interagir com o Visual Studio enquanto as solicitações de e/s acontecem em segundo plano.

### <a name="early-initialization-of-services-components"></a>Inicialização antecipada de serviços, componentes

Um dos padrões comuns na inicialização do pacote é inicializar serviços usados pelo ou fornecido por esse pacote no método de construtor ou inicializar pacote. Enquanto isso garante que serviços estão prontos para ser usado, ele também pode adicionar custos desnecessários para pacote de carregamento se esses serviços não são usados imediatamente. Em vez disso, esses serviços devem ser inicializados sob demanda para minimizar o trabalho feito na inicialização do pacote.

Para serviços globais fornecidos por um pacote, você pode usar métodos de AddService que usa uma função lentamente inicializar o serviço apenas quando solicitado por um componente. Para os serviços usados dentro do pacote, você pode utilizar Lazy<T> ou AsyncLazy<T> para garantir que os serviços são inicializados/consultada no primeiro uso.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Medir o impacto de auto carregado extensões usando o log de atividades

Começando na atualização 3 do Visual Studio de 2017, o log de atividades do Visual Studio agora contém entradas para o impacto no desempenho de pacotes durante o carregamento de inicialização e a solução. Para ver essas medidas, você precisa iniciar o Visual Studio com o parâmetro /log e abra o arquivo ActivityLog.xml.

No log de atividades, as entradas estará em fonte "Gerenciar Visual Studio Performance" e será semelhante ao seguinte:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Isso significa que o pacote com GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" gastou ms 2008 na inicialização do Visual Studio. Observe que o Visual Studio considera custo de nível superior como o número principal ao calcular o impacto de um pacote como seria o usuário savigs ver quando eles desabilitam a extensão do pacote.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Medir o impacto de auto carregado extensões usando PerfView

Enquanto a análise de código pode ajudar a identificar os caminhos de código que podem causar lentidão na inicialização do pacote, você também pode utilizar o rastreamento usando aplicativos como o PerfView para entender o impacto de um pacote de carga na inicialização do Visual Studio.

PerfView é uma ferramenta de rastreamento ampla de sistema que ajudarão você a entender os caminhos ativos em um aplicativo devido a uso da CPU ou de bloqueio de chamadas do sistema. Abaixo está um exemplo rápido na análise de uma extensão de exemplo usando o PerfView disponível no [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Código de exemplo:**

Este exemplo se baseia o exemplo de código a seguir, que é projetado para mostrar algumas causas comuns de atraso de caso:

```csharp
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

Depois de configurar o seu ambiente do Visual Studio com a extensão instalada, você pode gravar um rastreamento de inicialização abrindo o PerfView e abrindo a caixa de diálogo coletar no menu "Coletar".

![menu coletar perfview](media/perfview-collect-menu.png)

As opções padrão fornecerá pilhas de chamadas para o consumo de CPU, mas já que estamos interessados em tempo de bloqueio também, você também deve habilitar pilhas de "Tempo de threads". Quando as configurações estiver prontas, você pode clicar em "Iniciar coleta" e iniciar o Visual Studio depois de gravação é iniciada.

Antes de parar a coleta, você deseja certificar-se de que o Visual Studio está totalmente inicializado, a janela principal está completamente visível e se sua extensão tem qualquer partes da interface do usuário que mostram, automaticamente, eles também serão visíveis. Depois que o Visual Studio está totalmente carregado e sua extensão for inicializada, você pode interromper a gravação para analisar o rastreamento.

**Analisar um rastreamento com PerfView:**

Concluída a gravação PerfView será automaticamente abrir o rastreamento e opções.

Para os fins deste exemplo, estamos interessados principalmente no modo de exibição "Thread pilhas de tempo" que pode ser encontrado em "Grupo Avançado". Essa exibição mostrará o tempo total gasto em um thread por um método, incluindo o tempo de CPU e tempo bloqueado, como e/s de disco ou aguardando em identificadores.

 ![pilhas de tempo de thread](media/perfview-thread-time-stacks.png)

 Ao abrir a exibição de "Thread pilhas de tempo", você deve escolher o processo de "devenv" para iniciar a análise.

PerfView tem detalhadas orientação sobre como ler thread pilhas de tempo em seu próprio menu de ajuda para uma análise mais detalhada. Para fins deste exemplo, queremos filtrar ainda mais este modo de exibição somente incluindo pilhas com nossa thread de inicialização e o nome de módulo pacotes.

1. Defina "GroupPats" como texto vazio para remover qualquer agrupamento adicionado por padrão.
2. Defina "IncPats" para incluir a parte do seu nome de assembly e inicialização de Thread além de filtro de processo existente. Nesse caso, ele deve ser "devenv; Thread de inicialização; MakeVsSlowExtension".

Agora a exibição mostrará apenas custo associado com os assemblies relacionados à extensão. Nesta exibição, sempre listado na coluna "Inc" (Inclusive custo) do thread de inicialização está relacionado à nossa extensão filtrado e irá afetar a inicialização.

No exemplo acima alguns chamada interessante pilhas seria:

1. E/s usando a classe System.IO: ao custo inclusivo desses quadros pode não ser muito caro no rastreamento, eles são uma causa potencial de um problema já que a velocidade de e/s de arquivo irá variar de máquina para máquina.

  ![quadros de e/s do sistema](media/perfview-system-io-frames.png)

2. Bloqueio de chamadas aguardando outro trabalho assíncrono: nesse caso tempo inclusive representa a hora em que o thread principal é bloqueado após a conclusão de trabalho assíncrono.

  ![quadros de chamada de bloqueio](media/perfview-blocking-call-frames.png)

Um dos outros modos de exibição no rastreamento que serão úteis para determinar o impacto será as pilhas de carga"imagem". Você pode aplicar os mesmo filtros conforme aplicadas à exibição "Thread pilhas de tempo" e descobrir todos os assemblies carregados devido ao código executado por seu pacote carregado automaticamente.

É importante minimizar o número de assemblies carregados dentro de uma rotina de inicialização do pacote como cada assembly adicional envolve a e/s de disco extra que pode causar lentidão na inicialização consideravelmente em computadores mais lentos.

## <a name="summary"></a>Resumo

Inicialização do Visual Studio foi uma das áreas que continuamente chegar comentários. Nosso objetivo conforme mencionado anteriormente é para todos os usuários tenham uma inicialização consistente a experiência independentemente de componentes e extensões que esteja instalado e queremos trabalhar com os proprietários de extensão para ajudá-lo nos ajudar a alcançar essa meta. A orientação acima deve ser útil para entender o impacto extensões na inicialização e ou evitar a necessidade de automático de carga ou carregá-lo de forma assíncrona para minimizar o impacto na produtividade do usuário.

