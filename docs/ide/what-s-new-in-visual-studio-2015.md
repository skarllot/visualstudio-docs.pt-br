---
title: "O que h&#225; de novo no Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.StartPage.WhatsNew"
helpviewer_keywords: 
  - "Visual Studio, o que há de novo"
  - "novidades [Visual Studio]"
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
caps.latest.revision: 364
caps.handback.revision: 360
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# O que h&#225; de novo no Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bem\-vindo ao Visual Studio 2015, um conjunto integrado de ferramentas de produtividade do desenvolvedor, os serviços de nuvem e extensões que permitem que você e sua equipe criar ótimos aplicativos e jogos para a web, para a Windows Store, para a área de trabalho, para o Android e para iOS.  
  
 Esta página destaca alguns dos recursos mais importantes que são novos desde o Visual Studio 2013 RTM, incluindo recursos que foram introduzidos em uma das atualizações do Visual Studio 2013. Para obter uma lista completa das novidades no Visual Studio 2015, consulte o [notas de versão](https://www.visualstudio.com/news/vs2015-vs).  
  
 Para obter mais informações sobre os vários aprimoramentos e novos recursos no Visual Studio ALM, consulte [Novidades de gerenciamento de ciclo de vida do aplicativo no Visual Studio 2015](http://msdn.microsoft.com/pt-br/54b98a53-6083-4303-869a-8063d8fae938).  
  
## Uma nova experiência de instalação  
 [!INCLUDE[downloadvs](../ide/includes/downloadvs_md.md)]  
  
 A experiência de instalação do Visual Studio 2015 tem sido dividido em componentes para que você só precisa instalar as partes que você precisa. Isso torna a instalação mais rápida para muitos cenários comuns envolvendo desenvolvimento .NET ou da Web. Se você faz com outros tipos de desenvolvimento, como o desenvolvimento móvel entre plataformas, ou trabalhar em C\+\+ ou F \#, escolha **personalizado** instalação e, em seguida, escolha os componentes e SDKs de terceiros opcionais que você precisa. Você também pode instalar qualquer um dos componentes personalizados posteriormente. Por exemplo, se você escolher a instalação básica e, em seguida, tente criar um novo projeto C\+\+, você precisará baixar as ferramentas de desenvolvimento do C\+\+.  
  
 ![Visual Studio 2015 Setup Dialog](~/ide/media/vs2015_setup_screen.png "VS2015\_Setup\_screen")  
  
## Entrar em várias contas  
 Com o Visual Studio 2015, a novo simplificada experiência de logon foi projetada para simplificar o acesso a recursos online, mesmo quando você tiver várias contas do Visual Studio. Depois que você entrar no Visual Studio, você entrará automaticamente para todas as instâncias do Visual Studio 2015 e Blend no seu computador. Entrar automaticamente inicia o roaming as configurações para você. No Visual Studio 2015, sua conta é compartilhada entre recursos assim, contanto que tenha um bom token, você pode acessar suas contas do Visual Studio Team Services de **Team Explorer**, recursos e sites de sua assinatura do Microsoft Azure no Gerenciador de servidores. Você também verá os recursos do Azure na caixa de diálogo Novo projeto para projetos do Application Insights e você verá móvel do Azure, armazenamento do Azure, [Microsoft Office 365](http://msdn.microsoft.com/office/aa905340.aspx) e [Saleforce.com desenvolvedor](https://developer.salesforce.com/) contas no novo **Adicionar um serviço conectado** caixa de diálogo.  
  
 Você pode trabalhar com várias contas de usuário no Visual Studio ao adicioná\-los durante o processo ou por meio do Gerenciador de conta nova. Em seguida, você pode alternar entre essas contas em imediatamente quando se conectar a serviços ou acessar os recursos online. Visual Studio memoriza as contas que você adicionar para que possa usá\-los de qualquer instância do Visual Studio ou Blend. Visual Studio será também móvel na lista de contas \(embora nós não passarão suas credenciais valiosas\) com sua conta de personalização para que possa começar rapidamente a trabalhar com uma dessas contas em outro dispositivo. Obviamente, você poderá remover contas de caixa de diálogo Configurações de conta a qualquer momento. Para começar, consulte [Trabalhar com várias contas de usuário](../ide/work-with-multiple-user-accounts.md).  
  
 ![Account Manager](../ide/media/vs2015_accountmanager.gif "VS2015\_AccountManager")  
  
## Escolha sua plataforma de destino \(s\)  
 O Visual Studio 2015 oferece suporte ao desenvolvimento de dispositivos móveis de plataforma cruzada. Você pode escrever aplicativos e jogos que alvo iOS, Android e Windows e compartilham um código comum base, tudo a partir de IDE do Visual Studio. Você verá todos esses novos tipos de projeto no arquivo, caixa de diálogo Novo projeto.  
  
 E, claro, suporte para aplicativos de área de trabalho clássicos é melhor do que nunca, com muitas melhorias para linguagens, bibliotecas e ferramentas.  
  
### Aplicativos móveis de plataforma cruzada no c\# com Xamarin para Visual Studio  
 Xamarin é uma estrutura móvel que permite que você escreva código em c\# que associa nativamente para iOS e Android APIs. Microsoft juntou\-se em conjunto com o Xamarin na sua versão do Xamarin para Visual Studio, uma extensão que permite que você desenvolve para Windows Phone, iOS e Android em uma solução única com código compartilhado. Com o Xamarin, você usará um idioma e uma base de código com mínimas deltas entre as plataformas.  Xamarin para Visual Studio tem suporte no Visual Studio 2010 e posterior. É a edição inicial do Xamarin está incluído no Visual Studio 2015. Para começar, consulte [Criar aplicativos com interface de usuário usando o Xamarin no Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md).  
  
### Aplicativos móveis de plataforma cruzada em HTML\/JavaScript com o Apache Cordova  
 Visual Studio Tools for Apache Cordova é o resultado da forte colaboração entre a Microsoft e de código aberto Apache Cordova comunidade. As ferramentas permitem o desenvolvimento móvel entre plataformas usando HTML, CSS e JavaScript \(ou Typescript\). Você pode direcionar o Android, iOS e Windows com uma única base de código e aproveite a riqueza do IDE do Visual Studio incluindo JavaScript IntelliSense, o Explorador do DOM, Console do JavaScript, os pontos de interrupção, inspeções, locais, Just My Code e muito mais.  Com o Visual Studio Tools for Apache Cordova, seus aplicativos têm acesso aos recursos nativos do dispositivo em todas as plataformas através de plug\-ins que fornecem uma API de JavaScript. Para começar, consulte [Introdução às Ferramentas do Visual Studio para o Apache Cordova](../Topic/Get%20Started%20with%20Visual%20Studio%20Tools%20for%20Apache%20Cordova1.md).  
  
### Jogos móveis de plataforma cruzada em c\# com o Unity  
 Unity é uma plataforma amplamente usada para várias plataformas desenvolvimento de jogos 2D e 3D. Você pode escrever seu jogo em c\# e executá\-lo de forma nativa no iOS, Android, Windows Phone e muitas outras plataformas. Ferramentas do Visual Studio para Unity é uma extensão que integra o Unity com o IDE do Visual Studio. Com essa extensão, você obtém todos os recursos do depurador, além de recursos de produtividade que são projetados para desenvolvedores do Unity e Visual Studio IDE. Ferramentas do Visual Studio para Unity 2.0 Preview 2 adiciona suporte para Visual Studio 2015, além da um número de novos recursos, como uma melhor visualização para objetos nos locais e inspeção windows. A Microsoft adquiriu recentemente SyntaxTree, os criadores do Visual Studio Tools para Unity. Para baixar as ferramentas do Visual Studio para Unity 2.0 Preview 2 e para obter mais informações sobre o Visual Studio Tools para Unity, consulte [Visual Studio Tools para Unity 2.0](http://Aka.ms/vstu).  
  
### Aplicativos de plataforma cruzada e bibliotecas para C\+\+ nativo  
 C\+\+ é uma linguagem disponível nativamente pela maioria dos dispositivos móveis. Você pode usá\-lo para gravar bibliotecas de código compartilhado entre plataformas que podem ser criadas para vários destinos de plataforma móvel. Você pode até criar aplicativos móveis inteiros em C\+\+. Visual C\+\+ fornece as ferramentas para editar, compilar, implantar e depurar seu código de plataforma cruzada. Além dos modelos de aplicativos do Windows, você pode criar projetos de modelos para aplicativos Android atividade nativo, aplicativos iOS ou projetos de biblioteca de código compartilhado para várias plataformas que incluem aplicativos híbridos de Xamarin. IntelliSense específico da plataforma permite explorar APIs e gerar códigos corretos para destinos do Android, iOS ou Windows. Você pode configurar sua compilação para plataformas x86 ou ARM nativas e implantar seu código para um simulador de iOS ou dispositivos iOS em um Mac anexado à rede, para dispositivos Android conectados diretamente ou usar o emulador do Microsoft Visual Studio de alto desempenho para o Android para teste. Você pode definir pontos de interrupção, inspecione variáveis, exibir a pilha e percorrer o código C\+\+ no depurador do Visual Studio. Você pode compartilhar tudo, exceto o código específico da plataforma mais em várias plataformas de aplicativo e a desenvolver com uma solução no Visual Studio.  
  
 Para começar em C\+\+ de plataforma cruzada, consulte [Criar aplicativos móveis de plataforma cruzada com o Visual C\+\+](../misc/build-cross-platform-mobile-apps-with-visual-cpp.md)  
  
### Aplicativos universais do Windows para qualquer dispositivo Windows 10  
 Com a plataforma Windows Universal e nosso um núcleo do Windows, você pode executar o mesmo aplicativo em um dispositivo Windows 10 telefones para áreas de trabalho. Crie esses aplicativos universais do Windows com Visual Studio 2015 e as ferramentas de desenvolvimento de aplicativos Windows Universal.  
  
 ![Universal Windows Platform](../cross-platform/media/uwp_coreextensions.png "UWP\_CoreExtensions")  
  
 Execute o aplicativo em um telefone Windows 10, uma área de trabalho do Windows 10 ou um Xbox. É o mesmo pacote de aplicativo\! Com a introdução do Windows 10 unificado núcleo, um pacote de aplicativo pode executar todas as plataformas. Várias plataformas tem SDKs de extensão que você pode adicionar ao seu aplicativo para tirar proveito dos comportamentos específicos da plataforma. Por exemplo, uma extensão do SDK do mobile lida com o botão Voltar sendo pressionado em um Windows phone. Se você referenciar um SDK de extensão em seu projeto, basta Adicione verificações de tempo de execução para testar se esse SDK está disponível nessa plataforma. É como você pode ter o mesmo pacote de aplicativo para cada plataforma\!  
  
 Use c\#, Visual Basic, C\+\+ ou JavaScript para criar essas [aplicativos universais do Windows](http://msdn.microsoft.com/library/dn975273.aspx).  
  
### Web  
 O ASP.NET 5 é uma atualização importante para MVC, WebAPI e SignalR e executado no Windows, Mac e Linux.  O ASP.NET 5 foi projetado desde o início para cima para fornecer a que você com um .NET enxuta e combinável de pilha para a criação de aplicativos modernos baseados em nuvem. As ferramentas do Visual Studio 2015 está mais estreitamente integrada com ferramentas de desenvolvimento da web populares como Bower e pesado. Para começar, consulte as várias postagens de blog sobre o  [NET desenvolvimento para a Web e ferramentas de Blog](http://blogs.msdn.com/b/webdev/).  
  
### Área de trabalho clássica e da Windows Store  
 O Visual Studio 2015 continua a oferecer suporte a área de trabalho clássica e desenvolvimento da Windows Store. Como o Windows se desenvolve, Visual Studio evoluirá com ele.  No Visual Studio 2015, as bibliotecas e linguagens .NET, bem como C\+\+ fez avanços significativos que são aplicáveis a todas as versões do Windows.  
  
#### O .NET Framework  
 A Microsoft [!INCLUDE[net_v46](../ide/includes/net_v46_md.md)] oferece aproximadamente 150 novas APIs e 50 atualizados APIs para permitir mais cenários. Por exemplo, as coleções mais agora implementar <xref:System.Collections.Generic.IReadOnlyCollection%601> tornando\-os mais fáceis de usar. Além disso, o ASP.NET 5, mencionado anteriormente, oferece uma plataforma enxuta do .NET para a criação de aplicativos modernos baseados em nuvem.  
  
 Os aplicativos da Windows Store escritos em c\# que visam o .NET Framework agora podem tirar proveito do .NET nativo, que compila aplicativos para código nativo em vez de IL, e [!INCLUDE[net_v46](../ide/includes/net_v46_md.md)] também adiciona o RyuJIT, um compilador Just\-In\-Time \(JIT\) de 64 bits.  
  
 Os novos compiladores c\# e VB \("Roslyn"\) significativamente aceleram o tempo de compilação e fornecem APIs de análise de código abrangente. O Visual Studio 2015 tira proveito de Roslyn para fornecer mais refatorações incluindo embutido renomear, analisadores e correções rápidas.  
  
 As linguagens c\# e Visual Basic contém muitos aprimoramentos privilegiados no idioma principal e no suporte ao IDE. Todos esses aprimoramentos de somar para tornar sua experiência ainda mais intuitiva, conveniente e produtiva de codificação do .NET.  
  
 Para obter mais informações, consulte [O Que Há de Novo](../Topic/What's%20New%20in%20the%20.NET%20Framework.md) e [Blog .NET](http://blogs.msdn.com/b/dotnet/).  
  
#### C\+\+  
 O Visual C\+\+ fornece avanços significativos em C \+ \+ conformidade de 11\/14 idiomas, suporte para o desenvolvimento de dispositivo móvel entre plataformas, suportam para funções retomáveis e await \(atualmente planejados para padronização em C\+\+ 17\), aprimoramentos e bug corrige a biblioteca de C Runtime \(CRT\) e implementações do C\+\+ standard library \(STL\), redimensionáveis diálogos no MFC, novo compilador otimizações, criar melhor desempenho, novos recursos de diagnóstico e novas ferramentas de produtividade no editor de códigos.  
  
 Para obter mais informações, consulte [Novidades do Visual C\+\+](/visual-cpp/top/what-s-new-for-visual-cpp-in-visual-studio-2015) e [Blog do Visual C\+\+](http://blogs.msdn.com/b/vcblog/).  
  
## Barra de menus de visualização do dispositivo  
 Em projetos de plataforma Universal do Windows, a barra de menus da visualização de dispositivo permite que você veja como a interface do usuário baseada em XAML será renderizado em vários tamanhos de tela.  
  
 ![Device Preview menu](../ide/media/vs2015_device_preview.png "vs2015\_device\_preview")  
  
## Diagnóstico de gráficos do Visual Studio  
 Desde o Visual Studio 2013, Visual gráficos Studio diagnóstico adicionou muitos recursos novos, incluindo análise de quadro, suporte do Windows Phone, edição de sombreador e aplica e a linha de comando capturam ferramentas. Ele também adicionou suporte para depuração de aplicativos DirectX12. Para obter mais informações, consulte [Diagnóstico de gráficos do Visual Studio](../debugger/visual-studio-graphics-diagnostics.md).  
  
## Conectar a serviços  
 O Visual Studio 2015 torna mais fácil do que nunca para conectar seu aplicativo para serviços.  O Assistente para adicionar serviço conectado configura seu projeto, adiciona o suporte a autenticação necessária e baixa os pacotes do NuGet necessários para você começar a codificação com seu serviço rapidamente e sem complicações. O Assistente para adicionar serviço conectado também se integra com o novo gerente de conta para tornar mais fácil trabalhar com várias contas de usuário e assinaturas. No Visual Studio 2015, o suporte para os serviços a seguir é fornecido fora da caixa \(supondo que você tenha uma conta\):  
  
1.  Serviços móveis do Azure  
  
2.  Armazenamento do Azure  
  
3.  Office 365 \(email, contatos, calendários, arquivos, usuários e grupos\)  
  
4.  A equipe de vendas  
  
 Novos serviços serão adicionados continuamente, e você pode descobrir os clicando no "localizar novos serviços link" no assistente.  
  
 ![Add Connected Services Dialog](~/ide/media/vs2015_addconnectedservicedialog.png "VS2015\_AddConnectedServiceDialog")  
  
## Projetar sua interface do usuário  
 A experiência do Blend para criar interfaces do usuário XAML foi aprimorada significativamente. Blend foi completamente remodelado para fornecer uma interface do usuário mais intuitiva, mais poderosos recursos de edição de XAML incluindo IntelliSense e melhor integração com o Visual Studio. Para obter mais informações, consulte [Criando o XAML no Visual Studio e no Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md).  
  
## Suporte à depuração de plataforma cruzada  
 Você pode usar o Visual Studio para criar e depurar aplicativos móveis nativos que são executados em dispositivos Android, iOS e Windows. Use o [emulador do Visual Studio para Android](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx), ou conectar um dispositivo e depurar seu código diretamente no Visual Studio.  
  
-   **JavaScript \/ Cordova**. Use o [Visual Studio Tools for Apache Cordova](http://msdn.microsoft.com/library/dn879821\(v=vs.140\).aspx) para criar aplicativos nativos para o Windows, iOS e Android com JavaScript.  
  
     [Depurar seu aplicativo](../Topic/Debug%20Your%20App%20Built%20with%20Visual%20Studio%20Tools%20for%20Apache%20Cordova.md) na biblioteca do MSDN é uma visão detalhada de suporte para Cordova de depuração do Visual Studio.  
  
-   **C\# \/ Xamarin**. Use [Xamarin](http://msdn.microsoft.com/library/dn879698\(v=vs.140\).aspx) para criar aplicativos nativos para o Windows, iOS e Android no Visual Studio com c\#.  
  
     [Depuração](http://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/debugging_in_xamarin_ios/) \(iOS\) e [Depurar no dispositivo](http://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debugging_with_xamarin_android/) no [guias do desenvolvedor Xamarin](http://developer.xamarin.com/guides) descrevem a experiência de depuração.  
  
-   **C\+\+ \/ Android**. Use o [Visual C\+\+ para desenvolvimento móvel de plataforma cruzada](http://msdnstage.redmond.corp.microsoft.com/library/dn872463\(v=vs.140\).aspx) modelos junto com as ferramentas de terceiros, como o [NDK do Android](https://developer.android.com/tools/sdk/ndk/index.html) para criar aplicativos nativos para o Windows e Android.  
  
## Depuração e diagnóstico  
 Para obter informações sobre o que há de novo na depuração, consulte [O que há de novo no depurador no Visual Studio 2015](../debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md).  
  
 Para obter informações sobre o que há de novo no diagnóstico, consulte [O que há de novo nas ferramentas de criação de perfil](../profiling/what-s-new-in-profiling-tools.md).  
  
 A seguir é nova ou aprimorados ferramentas que executam diferentes tipos de análise e diagnóstico no seu código:  
  
### PerfTips  
 PerfTips exibir o tempo de execução dos métodos durante a depuração, permitindo que você identifique rapidamente gargalos sem a necessidade de chamar o criador de perfil. Para começar, consulte [PerfTips: informações de desempenho em geral durante a depuração com o Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx)  
  
### Lista de erros  
 A lista de erros agora oferece suporte à filtragem em qualquer coluna. Ele também mostra uma exibição de erros, avisos e análise de código ao vivo em sua solução inteira de c\# ou Visual Basic conforme você digita, mesmo quando uma alteração de código produz milhares de avisos. A nova lista de erros é compatível com o back com uso existente. Para obter mais informações, consulte [Janela Lista de Erros](../ide/reference/error-list-window.md).  
  
### Ferramenta de uso GPU  
 A ferramenta de uso de GPU ajuda a coletar e analisar dados de uso GPU no DirectX aplicativos e jogos e solucionar problemas se afunilamentos de desempenho são originadas na CPU ou GPU. Para começar a usar a ferramenta, consulte o [postagem de blog de equipe do Visual C\+\+](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx).  
  
## Análise de código ao vivo \(lâmpadas\)  
 O novo compilador Roslyn para c\# e Visual Basic fornece não só os tempos de compilação — ele também permite que completamente novos cenários como análise de código ao vivo, que fornecem avançado e personalizável comentários e sugestões diretamente dentro do editor de código, à medida que você digita. No Visual Studio 2015, lâmpadas exibir na margem esquerda \(ao usar o teclado\) ou uma dica de ferramenta \(quando passar o mouse sobre um erro com o mouse\). A lâmpada informa em tempo real que o compilador \(possivelmente usando um conjunto de regras personalizado\) detectou um problema no seu código e também tem uma sugestão para corrigir o problema. Quando você vir uma lâmpada, clique para sugestões acionáveis.  
  
 ![Light Bulbs in Visual Studio Code Editor](../ide/media/vs2015_lightbulbs.png "VS2015\_LightBulbs")  
  
## Aproveitar esses aprimoramentos adicionais do IDE  
  
### Configurações sincronizadas \(configurações de Roaming\)  
 Visual Studio 2013 apresentou configurações sincronizadas para algumas das configurações mais comumente configuradas como o Editor de texto, Keybindings, tema e fontes e cores, inicialização e Aliases de ambiente.  O Visual Studio 2015 aprimora essa experiência por sincronizar mais de suas configurações e sincronizar as configurações de toda a família do Visual Studio de aplicativos, como Professional, Enterprise, SKUs Express e mesclagem. Quando você entrar no Visual Studio 2015 pela primeira vez com a mesma conta que você usou no Visual Studio 2013, você verá as configurações sincronizadas aplicadas do Visual Studio 2013. Você pode acessar as configurações digitando "sincronização" no **início rápido**, ou navegar até **Ferramentas \> Opções \> ambiente \> configurações sincronizadas**.  
  
### Atualizações automáticas de extensão  
 As extensões do Visual Studio instaladas agora serão automaticamente atualizadas quando uma nova versão está disponível na Galeria do Visual Studio. Consulte [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md) para obter detalhes sobre como você pode personalizar a extensão automática de atualizações.  
  
### Menus de caso de título  
 Você falou, nós escutamos. Menus do Visual Studio são novamente capitalização de título por padrão. No entanto, se você realmente deseja o estilo todas em maiúsculas, você pode configurá\-lo no início ou no **Ferramentas \> Opções \> geral** página de propriedades:  
  
 ![Visual Studio 2015 Title Case Main Menu Commands](../ide/media/vs2015_mainmenu.png "VS2015\_MainMenu")  
  
### Imagens de alta resolução e suporte a toque  
 O IDE do Visual Studio agora tem imagens de alta resolução true em telas mais densos \(em áreas como menus, barras de comando de janela de ferramentas e menus de contexto e em alguns projetos no Gerenciador de soluções\). E, em uma tela sensível ao toque na janela do editor de código do Visual Studio, você pode usar gestos de agora, como toque e segure a tecla, aperte, toque e assim por diante para aplicar zoom, role, selecione o texto e invocar menus de contexto.  
  
 ![Touch support in editor](../ide/media/vs2015_touchsupport.png "VS2015\_TouchSupport")  
  
### Layouts personalizados  
 Você pode criar o repositório e se movem layouts de janela personalizados. Por exemplo, você pode definir um layout preferido para uso em seu computador desktop e layout diferente para uso em um laptop ou dispositivo de tela pequena. Ou talvez você prefira um layout para um projeto de interface do usuário e outro para um projeto de banco de dados. Associações de teclas permitem alternar rapidamente entre layouts. Esses layouts são disponibilizados em qualquer instância do Visual Studio quando você está conectado. Para obter mais informações, consulte [criar layouts de janela personalizados](../misc/create-custom-window-layouts.md).  
  
 ![Visual Studio Custom Layout menu item](../ide/media/vs2015_customlayout.png "VS2015\_CustomLayout")  
  
### Hub de notificação  
 A interface do usuário para o hub de notificação foi otimizada para torná\-lo mais fácil verificar rapidamente. Tipos adicionais de notificações foram adicionados como problemas de desempenho, problemas de processamento e falhas, e você agora pode informar ao Visual Studio para parar de mostrar uma notificação. Para obter mais informações, consulte [Visual Studio notificações](../ide/visual-studio-notifications.md).  
  
### CodeLens: Localizar o que aconteceu com seu código \(apenas para edições Enterprise e Professional\)  
 Mantenha o foco no trabalho enquanto você encontrar informações sobre seu código \- sem sair do editor. Você pode revisar as alterações e outro histórico de itens de trabalho, bugs, revisões de código, e assim por diante para o código que é armazenado no Visual Studio Team Services \(VSTS\) ou no Team Foundation Server \(TFS\).  
  
 No Visual Studio Enterprise e no Visual Studio Professional, agora você pode:  
  
-   Obtenha o histórico para um arquivo de todo código no editor do Visual Studio.  
  
     ![CodeLens: Get code file details](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  
  
-   Ver um gráfico que mostra as pessoas que alteraram seu código. Isso pode ajudá\-lo a encontrar padrões nas alterações da sua equipe e avaliar seu impacto.  
  
     ![CodeLens: See code changes history as a graph](~/ide/media/codelens.png "CodeLens")  
  
-   Ver facilmente quando seu código foi alterado pela última vez.  
  
-   Localize alterações em outras ramificações que afetam seu código.  
  
 Consulte [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).  
  
### Design e modelagem de ferramentas \(apenas Enterprise edition\)  
 **Gráficos de dependência e mapas de código**  
  
 No Visual Studio Enterprise, quando você quiser entender dependências específicas no seu código, exiba\-os Criando mapas de código. Em seguida, você pode navegar essas relações usando o mapa, que aparece ao lado de seu código. Mapas de código também podem ajudar a manter o controle de seu local no código enquanto você trabalha ou depura código, para que seja necessário ler menos código enquanto você aprender mais sobre o design do seu código.  
  
 Nesta versão, fizemos os menus de atalho para elementos de código e links muito mais fácil de usar, agrupando comandos em seções relacionadas a selecionar, editar, gerenciar grupos e alterando o layout do conteúdo do grupo. Observe também que os projetos de teste são exibidos em um estilo diferente de outros projetos e que atualizamos os ícones de elementos no mapa para versões mais adequadas.  
  
 ![Show selected items on a new code map](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
 Outros aprimoramentos incluem:  
  
-   **Aprimorado diagramas de cima para baixo**. Para médias e grandes soluções do Visual Studio, agora você pode usar um menu de arquitetura simplificado para obter um código mais útil mapas para sua solução. Os assemblies da sua solução são agrupados pelas pastas de solução, você pode vê\-los em contexto e aproveitar o esforço feito para estruturar a solução. Você verá imediatamente projeto e referências de assembly e os tipos de link são exibidos. Além disso, os assemblies externos à solução são agrupados de maneira mais compacta.  
  
-   **Projetos de teste têm estilo diferente e podem ser filtrados**. Você pode agora mais fácil e rapidamente identificar projetos de teste no mapa porque eles têm estilos diferentes. Eles podem também ser filtrados para que você possa se concentrar no código de trabalho do aplicativo.  
  
-   **Simplificado links de dependência externa**. Links de dependência não representam a herança de System. Object, ValueType, System. Enum e System. Delegate, que facilita ver dependências externas no mapa de códigos.  
  
-   **'Drill\-in into dependency links' leva os filtros em consideração**. Você obtém um diagrama simples e útil quando expande para compreender as contribuições para um link de dependência. O diagrama é menos desorganizado e leva em consideração as opções que você selecionou de filtragem de link.  
  
-   **Elementos de código são adicionados a um mapa de código com contexto**. Como os diagramas agora aparecem com contexto \(até assembly e solução de pasta em que você pode filtrar se necessário\), que obter diagramas mais eficientes ao arrastar e soltar elementos de código do Gerenciador de soluções, Class View, pesquisador de objetos; ou, quando selecionar elementos no Gerenciador de soluções e selecionando mostram no mapa de código.  
  
-   **Obter código reativo mais rapidamente mapeia**. Arrastar e soltar operações produzem um resultado imediato, e os links entre os nós são criados com muito mais rapidez, sem afetar as operações subsequentes iniciada pelo usuário, como expandir um nó ou solicitar mais nós. Quando você cria mapas de código sem compilar a solução, todos os casos de canto, como quando os assemblies não são compilados — agora são processados.  
  
-   **Ignorar a recompilação de sua solução.** Fornece um melhor desempenho durante a criação e edição de diagramas.  
  
-   **Filtrar grupos e nós de elemento de código**. Organizar rapidamente seus mapas mostrando ou ocultando elementos de código com base em sua categoria, bem como pelo agrupamento de elementos de código por pastas de solução, assemblies, namespaces, pastas de projeto e tipos.  
  
-   **Filtre relações para facilitar a leitura de diagramas**. Filtragem de link agora também se aplica para cruzar os links de grupo, o que torna o trabalho com a janela de filtros menos intrusivo que do que era nas versões anteriores.  
  
-   **Criar diagramas da exibição de classe e Pesquisador de objetos**. Arraste e solte arquivos e assemblies em um novo ou um mapa existente do windows de modo de exibição de classe e Pesquisador de objetos.  
  
 Consulte [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md).  
  
 **Outras alterações de design e modelagem nesta versão:**  
  
-   **Diagramas de camada**. Atualize esses diagramas usando o modo de exibição de classe e Pesquisador de objetos. Para atender aos requisitos de design de software, use diagramas de camada para descrever as dependências desejadas para seu software. Manter código consistente com o design encontrando o código que não atende a essas restrições e validando códigos futuros com essa linha de base.  
  
-   **Diagramas UML**. Você não pode mais criar diagramas de sequência e diagramas de classe UML no código. Mas você ainda criar esses diagramas usando novos elementos UML.  
  
-   **Architecture Explorer**. Você não pode usar o Explorer de arquitetura para criar diagramas. Mas você ainda pode usar o Gerenciador de soluções.  
  
## Ferramentas de extensibilidade do Visual Studio  
 Nunca foi tão fácil instalar as ferramentas de extensibilidade de Visual Studio \(SDK do VS e modelos\), que agora estão incluídos como um componente opcional durante a instalação.  As ferramentas de extensibilidade permitem aos desenvolvedores escrever extensões para personalizar e adicionar recursos para o Visual Studio. Para obter mais informações sobre extensibilidade do Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
 Se você deseja incluir as ferramentas de extensibilidade com sua instalação personalizada, você pode encontrá\-los em **recursos \/ ferramentas comuns \/ ferramentas de extensibilidade do Visual Studio**.  Você também pode instalar as ferramentas de extensibilidade posteriormente abrindo o **novo projeto** caixa de diálogo e selecionar o **instalar ferramentas do Visual Studio Extensibility** item sob **Visual c\# \/ extensibilidade**.  
  
## Envie comentários  
 Por que enviar comentários à equipe do Visual Studio? Como os comentários dos clientes, levar a sério. Na verdade, vamos examinar cada parte de comentários que entram em nosso sistema de comentários. Seus comentários unidades muito do que fazemos.  
  
### Enviar um Smiley  
 Nos dizendo que você como nos ajuda a entender quando podemos atender ou superar as suas expectativas. Quando estamos Projetando e implementando novos recursos, podemos usar dados sobre os recursos que você deseja ajudar com nossas decisões de design. Portanto, se você gosta de um recurso no Visual Studio, conte\-nos sobre ele. É fácil e você pode fazer isso diretamente de dentro do IDE.  
  
 A face de smiley amarelo na barra de título, diga\-no que você gostou clique apenas o **Enviar um Smiley** botão.  
  
 Isso é tudo\! Podemos vai rotear seus comentários para a equipe correta onde eles pat próprios na parte traseira e começar a pensar em maneiras para encantar ainda mais rapidamente.  
  
### Enviar um rosto triste  
 Ouvindo em que precisamos fazer melhorias no produto nos ajuda a gerenciar nossa lista de pendências, concentrando\-se primeiro as coisas mais importantes para nossos clientes. Se houver algo que é bugging você, conte\-nos sobre ele usando o **Enviar um rosto triste** recurso de diretamente do IDE. Fizemos isso um processo muito simples demais:  
  
 A face de smiley amarelo na barra de título, clique em **Enviar um rosto triste**. Diga\-no que você não gostou, em seguida, clique em enviar um rosto triste botão. Para obter mais informações, consulte [Fale conosco](../ide/talk-to-us.md).  
  
### Relatório de panes, interrupções e problemas de desempenho  
 Às vezes, uma rápida observação em um rosto triste simplesmente não é suficiente para transmitir o impacto total de algo que não desejar. Para os horários quando você tem um problema de desempenho, falhas ou suspensão, você pode compartilhar facilmente etapas de reprodução, despejos de memória e arquivos de rastreamento usando a caixa de diálogo é exibida depois que você envia um rosto triste.  
  
 Primeiro, envie um rosto triste conforme descrito acima. Na caixa de diálogo pop\-up, você pode marcar seus comentários com qualquer uma das marcas padrão ou criar sua própria marca. Marcas nos ajudam a rotear seus comentários para a equipe de recursos apropriado. No **Escolha uma categoria** lista suspensa, selecione a opção que representa o problema estiver relatando e siga as etapas para reproduzir o problema. Etapas detalhadas sobre como usar o Visual Studio para fornecer comentários também estão disponíveis. Para obter mais informações, consulte [O Visual Studio envia instruções de forma agradável](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md).  
  
### Acompanhar o seu problema em conectar\-se  
 Se você quiser controlar o status dos seus comentários do Visual Studio 2015, vá para [conectar](http://connect.microsoft.com/) e denuncie o bug lá. Após relatar o erro, você poderá retornar ao conectar\-se para controlar seu status.  
  
## Consulte também  
 [Compilar aplicativos de plataforma cruzada com o Apache Cordova](../Topic/Build%20cross-platform%20apps%20with%20Visual%20Studio%20Tools%20for%20Apache%20Cordova.md)   
 [Criar aplicativos com interface de usuário usando o Xamarin no Visual Studio](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)   
 [Criar aplicativos móveis de plataforma cruzada com o Visual C\+\+](../misc/build-cross-platform-mobile-apps-with-visual-cpp.md)   
 [Gerar testes de unidade para seu código com IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md)   
 [Trabalhar com várias contas de usuário](../ide/work-with-multiple-user-accounts.md)   
 [Criar layouts de janela personalizados](../misc/create-custom-window-layouts.md)   
 [Realizar ações rápidas com lâmpadas](../ide/perform-quick-actions-with-light-bulbs.md)   
 [Novidades no Gerenciamento do Ciclo de Vida do Aplicativo no Visual Studio  2015](http://msdn.microsoft.com/pt-br/54b98a53-6083-4303-869a-8063d8fae938)