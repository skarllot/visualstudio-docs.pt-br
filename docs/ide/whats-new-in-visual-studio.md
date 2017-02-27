---
title: Novidades no Visual Studio 2017 RC | Microsoft Docs
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a

---
# <a name="what39s-new-in-visual-studio-2017"></a>Novidades no Visual Studio 2017
Bem-vindo ao Visual Studio 2017 RC, um pacote integrado de ferramentas de produtividade do desenvolvedor, de serviços de nuvem e de extensões que permitem que você e sua equipe criem ótimos aplicativos e jogos para a Web, para a Windows Store, para a área de trabalho, para o Android e para iOS.  

Nesta RC (versão Release Candidate) da nossa versão mais recente do Visual Studio, nos concentramos em aprimoramentos de desempenho e produtividade. Em termos de desempenho, fizemos o Visual Studio iniciar mais rápido, ser mais dinâmico e usar menos memória do que nunca. Em relação à produtividade, adicionamos ou atualizamos recursos que podem ajudá-lo a ser mais eficiente ao usar o Visual Studio.

> [!TIP]
> Para ver nossa nova RC em ação, assista ao vídeo [Novidades no Visual Studio](https://channel9.msdn.com/events/connect/2016/159) no Channel 9.   

Aqui está um resumo de alto nível das alterações que fizemos:

* **Produtividade Aumentada**. Aprimoramentos na navegação do código, no IntelliSense, na refatoração, nas correções do código e na depuração economizam tempo e esforço nas tarefas diárias, independentemente da linguagem ou da plataforma. Além disso, para as equipes que adotam o DevOps, o Visual Studio 2017 simplifica o loop interno do desenvolvedor e agiliza o fluxo do código com recursos em tempo real novinhos, como o teste de unidade dinâmico e a validação da dependência de arquitetura em tempo real.
* **Princípios básicos redefinidos**.  Há um foco renovado para aprimorar a eficiência das tarefas básicas que os desenvolvedores encontram diariamente. De uma instalação nova, leve e modular adequada às necessidades de um desenvolvedor, um IDE mais rápido da inicialização ao desligamento e um novo modo de exibir, editar e depurar qualquer código sem projetos nem soluções, o Visual Studio 2017 ajuda os desenvolvedores a manter o foco na visão global.
* **Desenvolvimento do Azure simplificado**. Pacote interno de ferramentas do Azure que permite aos desenvolvedores criar facilmente aplicativos para a nuvem da plataforma Microsoft Azure. O Visual Studio facilita configurar, compilar, depurar, empacotar e implantar aplicativos e serviços no Microsoft Azure diretamente do IDE.
* **Desenvolvimento móvel de cinco estrelas**. Com ferramentas avançadas de depuração e criação de perfil, e com recursos de geração de teste de unidade, o Visual Studio 2017 com Xamarin torna mais rápido e fácil do que nunca para os desenvolvedores compilar, conectar e ajustar os aplicativos móveis para o Android, iOS e Windows. Os desenvolvedores também podem escolher desenvolver aplicativos móveis com o Apache Cordova ou com o desenvolvimento de bibliotecas entre plataformas do Visual C++, tudo isso no Visual Studio.  

E aqui estão mais detalhes sobre as nossas alterações mais importantes.

> [!NOTE]
> Para obter uma lista completa dos novos recursos e funcionalidades no Visual Studio 2017 RC e sua Atualização RC subsequente, consulte as [Notas de versão](https://www.visualstudio.com/news/vs2015-vs). E para obter uma lista de problemas e soluções alternativas, consulte a seção [Problemas conhecidos](https://www.visualstudio.com/news/vs2015-vs#knownissues) das Notas de versão.   

## <a name="performance-improvements"></a>Melhorias de desempenho

### <a name="a-new-setup-experience"></a>Uma nova experiência de instalação  
[Baixar o Visual Studio Enterprise 2017 RC](https://aka.ms/vs/15/preview/vs_enterprise) ou [Verificar os requisitos de sistema do Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 Reformulamos a experiência de instalação do Visual Studio para tornar ainda mais fácil instalar somente os recursos que você precisa e quando você precisa. Também reduzimos os volumes mínimos, para que o Visual Studio seja instalado mais rapidamente e com menos impacto ao sistema. Além disso, ele também se desinstala completamente.

 A alteração mais importante que você verá ao instalar o Visual Studio é a nova experiência de instalação. Na guia **Cargas de trabalho**, você verá opções de instalação que são agrupadas para representar estruturas, linguagens e plataformas comuns, abrangendo tudo, desde o desenvolvimento da área de trabalho do .NET à ciência de dados com R, Python e F#.  

 ![Caixa de Diálogo de instalação do Visual Studio 2017 RC](../ide/media/willow1.png "VS2017RC_Setup_screen")

Escolha as cargas de trabalho que você precisa e altere-as quando necessário. A menor instalação tem apenas algumas centenas de megabytes, mas ainda tem suporte para edição de código básico em mais de vinte linguagens, bem como controle do código-fonte.

Também adicionamos diferentes maneiras para instalar o Visual Studio. Deseja escolher seus próprios componentes em vez de usar cargas de trabalho? Basta selecionar a guia **Componentes individuais** no instalador. Deseja instalar Pacotes de Idiomas sem precisar alterar também a opção de idioma do Windows? Escolha a guia **Pacotes de idiomas** do instalador.  

Para saber mais sobre a nova experiência de instalação, incluindo instruções que mostram a instalação passo a passo, consulte nossa página [Instalar o Visual Studio](../install/install-visual-studio.md).


### <a name="start-visual-studio-faster"></a>Iniciar o Visual Studio mais rápido
Se o Visual Studio detectar que o tempo de inicialização do IDE está lento, ele fornecerá um novo Controle de Desempenho do Visual Studio para ajudá-lo a acelerar as coisas. O Controle de Desempenho lista todas as extensões e janelas de ferramentas que estão causando lentidão na inicialização do IDE. Você pode usá-lo para melhorar o desempenho de inicialização, determinando quando iniciar as extensões ou se as janelas de ferramentas serão abertas na inicialização.

### <a name="decrease-solution-load-time"></a>Diminuir o tempo de carregamento da solução
O trabalho em soluções que contêm mais de 100 projetos não significa que você precisa trabalhar com todos os arquivos ou projetos de uma só vez. Agora você pode editar e depurar sem ter que aguardar o Visual Studio carregar todos os projetos. Para experimentar com projetos gerenciados, ative **Carregar Solução Leve** em Ferramentas-> Opções-> Projetos e Soluções.

  ![Caixa de diálogo de opções no Visual Studio 2017 RC](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "Caixa de diálogo opções do VS2017RC – Carregar Solução Leve")

### <a name="faster-on-demand-loading-of-extensions"></a>Carregamento sob demanda de extensões mais rápido
A ideia é simples: carregar extensões quando forem necessárias em vez de carregá-las quando o Visual Studio é iniciado. Primeiro, mudamos as nossas extensões Python e Xamarin para serem carregadas sob demanda e, em seguida, estamos trabalhando para fazer dessa mesma forma com todas as extensões fornecidas com o Visual Studio e extensões fornecidas por terceiros. Curioso para saber quais extensões afetam a inicialização, carga de solução e desempenho de digitação? Você pode ver essas informações em Ajuda -> Gerenciar desempenho do Visual Studio.

  ![Caixa de diálogo de opções no Visual Studio 2017 RC](../ide/media/vs2017ide-ManageVSperf.png "Caixa de diálogo de ajuda do VS2017RC – Gerenciamento de desempenho")

## <a name="productivity-improvements"></a>Aprimoramentos de produtividade

### <a name="sign-in-across-multiple-accounts"></a>Entrar através de várias contas  
Apresentamos um novo serviço de identidade no Visual Studio 2017 RC que permite que você compartilhe as contas de usuário entre as ferramentas de desenvolvedor da Microsoft, como o Team Explorer, as Ferramentas do Azure, a publicação da Windows Store e muito mais.

Além disso, você pode permanecer conectado por mais tempo. Não solicitaremos que você entre novamente a cada 12 horas. Para obter mais informações, consulte a postagem de blog [Menos solicitações de Entrada no Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gerenciar suas extensões com o Roaming Extension Manager
Agora é ainda mais fácil configurar cada ambiente de desenvolvimento com suas extensões favoritas ao entrar no Visual Studio. Nosso novo Roaming Extension Manager controla todas as suas extensões favoritas, criando uma lista sincronizada na nuvem.  

Para ver uma lista de suas extensões no Visual Studio, clique em Ferramentas > Extensões e Atualizações e, em seguida, clique em Roaming Extension Manager.

![Visual Studio 2017 – Caixa de diálogo Extensões e Atualizações](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017 – Ferramentas > Caixa de diálogo Extensões e Atualizações")

O Roaming Extension Manager rastreia todas as extensões instaladas, mas você pode escolher quais você deseja adicionar à lista de Roaming.

![Visual Studio 2017 – Caixa de diálogo Extensões e Atualizações](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 – Roaming Extension Manager")

Ao usar o Roaming Extension Manager, você perceberá 3 tipos de ícones em sua lista:
* ![Ícone de Roaming](../ide/media/vs2017ide-roamedicon.png "Ícone de Roaming") ***Ícone de Roaming***: uma extensão que faz parte dessa Lista de Roaming, mas não está instalada em seu computador.
  (Você pode instalá-las usando o botão **Download**).
* ![Ícone de Roaming e Instalado](../ide/media/vs2017ide-roamedinstalledicon.png "Ícone de Roaming e Instalado") ***Ícone de Roaming e Instalado***: todas as extensões que fazem parte dessa Lista de Roaming e que estão instaladas em seu ambiente de desenvolvimento.
  (Se você decidir que não deseja usar perfil móvel, poderá remover essas extensões usando o botão **Parar Roaming**).
* ![Ícone de Instalado](../ide/media/vs2017ide-installedicon.png "Ícone de Instalado") ***Ícone de Instalado***: todas as extensões que estão instaladas nesse ambiente, mas não fazem parte da sua Lista de Roaming.
  (Você pode adicionar extensões à Lista de Roaming usando o botão **Iniciar Roaming**).

Esses ícones mostram o status atual da sua lista. Você pode ter qualquer extensão em qualquer estado, então personalize de acordo com sua vontade! Ou então, deixe que fazemos isso para você! Qualquer extensão que você baixar enquanto estiver conectado é adicionada à lista como **Roaming e Instalado** e faz parte da sua Lista de Roaming, fornecendo acesso de qualquer computador!

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Experimente validação de dependência de arquitetura em tempo real e teste de unidade em tempo real

No Visual Studio Enterprise 2017 RC, se você configurou diagramas de Validação de Dependência (também conhecidos como Diagramas de camada), você pode ser notificado em tempo real sobre violações de regra de dependência de arquitetura enquanto digita o código no Editor de Código.

Os erros aparecem na Lista de Erros e os rabiscos no editor de texto mostram o local exato de uma violação. Agora há menor probabilidade de introduzir dependências indesejáveis.

![Validação da arquitetura em tempo real](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Validação de dependência de arquitetura em tempo real")

#### <a name="live-unit-testing"></a>Live Unit Testing:

O Live Unit Testing é um novo recurso que estamos introduzindo e que está presente apenas na edição Enterprise do Visual Studio. Esse recurso visualiza os resultados de teste de unidade e cobertura de código em tempo real no editor, enquanto você está codificando. Ele funciona com projetos em C#/VB para o .NET Framework e dá suporte a três estruturas de teste de MSTest, xUnit e NUnit.

### <a name="visual-studio-ide-enhancements"></a>Aprimoramentos no IDE do Visual Studio
#### <a name="interact-with-git"></a>Interagir com o Git:
Os controles no canto inferior do IDE do Visual Studio permitem que você confirme e publique rapidamente seus projetos no Git e gerencie seus repositórios do Git.

![Caixa de Diálogo de instalação do Visual Studio 2017 RC](../ide/media/vsIDE-GitInteraction.png "Git-tools-in-the-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Exibir e navegar no código com o Visualizador de Estrutura:
Um novo recurso chamado Visualizador de Estrutura está disponível no editor de código do Visual Studio. Esse recurso exibe diretrizes verticais entre áreas aninhadas do código, tornando mais fácil exibir e navegar através do seu código. Esse recurso está disponível para todas as linguagens com suporte de TextMate, bem como Visual C#, Visual Basic e XAML.

![Caixa de Diálogo de instalação do Visual Studio 2017 RC](../ide/media/vsIDE-StructureVisualizer.png "Structure-Visualizer-in-VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>Experimente um Navegar Para aprimorado:
Melhoramos a função Navegar Para. Simplificamos a janela Navegar Para e adicionamos suporte para caracteres de filtro adicionais, que permitem restringir suas pesquisas de código.

#### <a name="create-apps-in-even-more-programming-languages"></a>Criar aplicativos em mais linguagens de programação:
Você pode criar aplicativos no Visual Studio usando um número de linguagens de programação maior que nas versões anteriores e as soluções e projetos não são mais necessários. Seu código obtém colorização de sintaxe, preenchimento de declaração básico e, em alguns casos, Navegar Para e outros suportes. Se não há suporte para sua linguagem favorita, você pode criar suporte para ela usando Gramáticas TextMate.

### <a name="visual-c"></a>Visual C++
O Visual Studio 2017 RC traz muitas atualizações e correções para o ambiente do Visual C++. Corrigimos mais de 250 bugs e problemas relatados no compilador e nas ferramentas, muitas enviadas pelos clientes através do [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Também fizemos vários aprimoramentos para incluir a distribuição de Diretrizes do C++ Core com o Visual Studio, atualizando o compilador com a adição de suporte aprimorado para recursos C++11 e C++, adicionando e atualizando funcionalidades nas bibliotecas do C++ e melhorando o desempenho do IDE do C++, das cargas de trabalho de instalação e muito mais.

Para obter detalhes completos, consulte nossa página [Novidades do Visual C++ no Visual 2017 RC](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  


### <a name="debugging-and-diagnostics"></a>Depuração e Diagnóstico
A depuração é mais rápida agora e não causa atrasos enquanto você está editando.

Por exemplo: em uma versão anterior do Visual Studio, apresentamos o que é conhecido como o processo de hospedagem para projetos do WPF, do Windows Forms e do Console Gerenciado, para tornar a depuração mais rápida, gerando um processo em segundo plano para usar na próxima sessão de depuração. Esse recurso bem-intencionado fazia com que o Visual Studio ficasse sem reposta durante alguns segundos ao parar a depuração ou ao usar o Visual Studio após o encerramento da sessão de depuração.

Desativamos o processo de hospedagem no Visual Studio de 2017 e otimizamos a depuração para que ele seja tão rápido quanto sem o processo de hospedagem e ainda mais rápido para os projetos que nunca usaram o processo de hospedagem (como projetos ASP.NET, Universal do Windows e C++).

#### <a name="run-to-click"></a>Executar com um Clique:
Agora, enquanto estiver depurando, você pode clicar no ícone ao lado de uma linha de código para executar essa linha. Não é mais necessário definir pontos de interrupção temporários a fim de realizar várias etapas para executar seu código e parar na linha que você deseja.

![Depuração do Visual Studio 2017 RC – Executar com um Clique](../ide/media/vs2017ide-RunToClick.png "Executar com um Clique a depuração e diagnósticos no Visual Studio 2017")

#### <a name="the-new-exception-helper"></a>O novo Auxiliar de Exceção:

Você pode usar o novo Auxiliar de Exceção para exibir suas informações de exceção em um instante em uma caixa de diálogo não modal compacta com acesso instantâneo às exceções internas.

Veja rapidamente o que foi nulo diretamente dentro do Auxiliar de Exceção ao diagnosticar uma NullReferenceException.

Também é possível excluir quebras em tipos de exceção que são lançados de módulos específicos, clicando na caixa de seleção para adicionar uma condição enquanto você estiver parado na exceção lançada.

![A nova caixa de diálogo Auxiliar de Exceção](../ide/media/vs2017ide-ExceptionHelper.png "A nova caixa de diálogo Auxiliar de Exceção")

Para obter mais informações, consulte a postagem de blog [Usando o novo Auxiliar de Exceção no Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

## <a name="talk-to-us"></a>Fale conosco  
 Por que enviar comentários à equipe do Visual Studio? Porque nós levamos a sério os comentários dos clientes. Orienta muito do que fazemos.  

Se você quiser fazer sugestões sobre como podemos aprimorar o Visual Studio ou relatar um problema, confira a página [Fale conosco](../ide/talk-to-us.md) para obter mais detalhes.  

### <a name="report-a-problem"></a>Relatar um problema  
 Às vezes, uma mensagem não é suficiente para transmitir o impacto total de um problema que você encontrou. Se você tiver um travamento, uma falha ou outro problema de desempenho, você poderá compartilhar facilmente conosco as etapas de reprodução e os arquivos de suporte (como capturas de tela e arquivos de rastreamento e arquivos de despejo com heap) usando a ferramenta **Relatar um Problema**. Para obter mais informações sobre como usar essa ferramenta, consulte a página [Como relatar um problema](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Acompanhar seu problema no Connect  
 Se você quiser acompanhar o status de seus comentários do Visual Studio, basta ir até o [Connect](http://connect.microsoft.com/) e reportar o bug lá. Depois que você reportar, é possível retornar ao Connect para acompanhar o status.  

## <a name="see-also"></a>Consulte também  
* [Novidades no Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Novidades no C#](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [Novidades para o Team Foundation Server](https://www.visualstudio.com/en-us/docs/whats-new)
* [Notas de Versão do Visual Studio](https://www.visualstudio.com/news/vs2015-vs)



<!--HONumber=Feb17_HO4-->


