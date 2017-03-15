---
title: "Recursos do IntelliTrace | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurando [Visual Studio ALM], IntelliTrace"
  - "depurando [Visual Studio ALM], gravando histórico de execução"
  - "IntelliTrace, depurando com eventos"
  - "IntelliTrace, depurando com eventos e informações de chamadas"
  - "IntelliTrace, desabilitando"
  - "IntelliTrace, ativando"
  - "IntelliTrace, navegando no histórico de eventos e chamadas"
  - "IntelliTrace, gravando histórico de execução"
  - "IntelliTrace, salvando sua sessão"
  - "IntelliTrace, iniciar depuração"
  - "IntelliTrace, desativar"
  - "IntelliTrace, ativar"
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 67
caps.handback.revision: 67
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Recursos do IntelliTrace
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar o IntelliTrace para registrar eventos e método chama seu aplicativo, que permite que você examine o estado \(pilha de chamadas e valores de variáveis locais\) em diferentes pontos na execução.  Comece a depuração como de costume \- IntelliTrace é ativado por padrão e você pode ver as informações IntelliTrace está gravando no novo**Ferramentas de diagnóstico**janela sob o**eventos**guia.  Selecione um evento e clique em**Ativar depuração de histórico**para ver a pilha de chamadas e locais registrados para este evento.  
  
 Para obter uma descrição passo a passo, consulte[Passo a passo: usando o IntelliTrace](../debugger/walkthrough-using-intellitrace.md).  
  
 IntelliTrace está disponível na edição Enterprise do Visual Studio, mas não nas edições do Visual Studio Professional ou da comunidade.  
  
 Para confirmar que o IntelliTrace esteja ativado, abra o**Ferramentas \/ opções \/ IntelliTrace**página de opções.  **Habilitar IntelliTrace**deve ser marcada por padrão.  
  
> [!NOTE]
>  O escopo de todas as configurações de**IntelliTrace**página de opções é o Visual Studio como um todo, soluções ou projetos não individuais.  Uma alteração nessas configurações se aplica a todas as instâncias do Visual Studio, depuração de todas as sessões e todos os projetos ou soluções.  
  
##  <a name="ChooseEvents"></a> Escolha os eventos que o IntelliTrace registra  
 Você pode ativar ou desativar o registro de eventos específicos do IntelliTrace.  
  
 Se você estiver depurando, pare a depuração.  Vá para**Ferramentas \/ opções \/ IntelliTrace \/ eventos do IntelliTrace**.  Escolha os eventos que você deseja que o IntelliTrace registrar.  
  
##  <a name="GoingFurther"></a> Coletar eventos do IntelliTrace e informações de chamada  
 Isso não é habilitado por padrão, mas o IntelliTrace poderá registrar chamadas de método com eventos.  Para habilitar a coleta do método chamadas vão para**Ferramentas \/ opções \/ IntelliTrace \/ geral**e selecione**eventos do IntelliTrace e informações de chamada**.  
  
 Isso permite que você consulte o histórico da pilha de chamadas e retroceda e avance por meio de chamadas em seu código.  O IntelliTrace registra dados como nomes de método, pontos de entrada e saída do método e determinados valores de parâmetros e valores de retorno.  
  
> [!TIP]
>  Essa opção não é habilitada por padrão porque ela adiciona uma sobrecarga considerável.  Não apenas tem IntelliTrace interceptar todas as chamadas de método que faz com que seu aplicativo, mas ela também precisa lidar com um conjunto maior de dados quando se trata de mostrá\-lo na tela ou persisti\-los no disco.  
>   
>  Você pode reduzir a sobrecarga de desempenho ao restringir a lista de eventos que o IntelliTrace registra e mantendo o número de módulos que você está coletando mínimo.  Para obter mais informações, consulte[Controlar a quantidade de informações gravadas pelo IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).  
  
### Usando a medianiz de navegação  
 Você pode usar a medianiz de navegação que aparece à esquerda da janela de código.  Se você não vir a medianiz de navegação, vá para**Ferramentas \/ opções \/ IntelliTrace \/ avançado**e selecione**Exibir a medianiz de navegação no modo de depuração**.  
  
 A medianiz de navegação permite que você mova a frente e para trás por meio de chamadas de métodos e eventos no modo de depuração histórico.  Para obter mais informações sobre depuração de histórico, consulte[Depuração de histórico](../debugger/historical-debugging.md).  Ele tem uma série de comandos:  
  
|||  
|-|-|  
|**Definir Contexto do Depurador Aqui**|Defina o contexto de depuração para o período de chamada onde ele aparece.<br /><br /> Esse ícone aparece somente na pilha de chamadas atual.|  
|**Voltar para o site de chamada**|Mova o ponteiro e o contexto de depuração para onde a função atual foi chamada.<br /><br /> Se você estiver no modo de depuração ao vivo, este comando ativa depuração de histórico.  Se você navegar de volta para o intervalo de execução original, depuração de histórico é desativado e depuração em tempo real está ativada.|  
|**Ir para chamada anterior ou para evento do IntelliTrace**|Mova o ponteiro e o contexto de depuração de volta para a chamada anterior ou evento.<br /><br /> Se você estiver no modo de depuração ao vivo, este comando ativa de depuração de histórico.|  
|**Entrar Em**|Passar para a função selecionada no momento.<br /><br /> Esse comando estará disponível somente quando você está no modo de depuração de histórico.|  
|**Ir para próxima chamada ou para evento do IntelliTrace**|Mova o ponteiro e o contexto de depuração para a próxima chamada ou evento para qual IntelliTrace dados existem.<br /><br /> Esse comando estará disponível somente quando você está no modo de depuração de histórico.|  
|**Ir para o modo ao vivo**|Retornar ao modo de depuração ao vivo.|  
  
### Procurar por uma linha ou um método no IntelliTrace  
 Você pode procurar métodos somente quando as informações de chamada de método tem sido habilitadas.  Você pode pesquisar histórico do IntelliTrace para uma linha específica ou um método.  Durante a execução do depurador é interrompida, clique dentro do corpo da função para ver o menu de contexto e clique em**pesquisa para esta linha no IntelliTrace**ou**pesquisa para este método no IntelliTrace**.  
  
###  <a name="ControlCallData"></a> Controlar a quantidade de informações gravadas pelo IntelliTrace  
 Por padrão, o IntelliTrace registra informações para todos os módulos usados pela solução.  Você pode definir o IntelliTrace para informações de chamada de registro somente para os módulos que lhe interessam.  Em**Ferramentas \/ opções \/ IntelliTrace \/ módulos**você pode especificar os módulos para incluir ou módulos a serem excluídos do IntelliTrace.  IntelliTrace coletará apenas os eventos originados dos módulos que você especificou e chamadas de método que ocorreram nos módulos que lhe interessam.  
  
 Para adicionar vários módulos, use o caractere curinga \* no início ou no final da cadeia de caracteres.  Para nomes de módulos, use nomes de arquivos, e não nomes de assembly.  Caminhos de arquivo não são aceitos.  
  
 Tente manter o número de módulos em um mínimo.  Obter um desempenho melhor porque há menos dados a serem coletados.  Você também obtém menos ruído na interface do usuário porque há menos dados para percorrer.  
  
##  <a name="SaveSession"></a> Salvando dados do IntelliTrace em arquivo  
 Você pode salvar os dados que o IntelliTrace coletou vai**Debug \/ IntelliTrace \/ salvar a sessão do IntelliTrace**enquanto você está depurando o aplicativo está no estado de interrupção.  O item de menu está desativado e você não poderá salvar os dados que IntelliTrace coletou se o aplicativo ainda está em execução ou se você parar a depuração.  
  
 Você pode configurar o IntelliTrace para salvar um arquivo automaticamente acessando**Ferramentas \/ opções \/ IntelliTrace \/ avançado**e selecionando**gravações de repositório IntelliTrace nesse diretório**.  Você também pode configurar um tamanho definido para o arquivo gerado, o que faz com que o IntelliTrace gravar os dados mais antigos quando ficar sem espaço.  Visual Studio cria dois arquivos para cada sessão do IntelliTrace quando eles são salvos automaticamente e o Visual Studio \(vshost.exe\) do processo de hospedagem está ativado.  
  
> [!TIP]
>  Para economizar espaço em disco, desative a salvar arquivos automaticamente quando você não precisa mais.  Todos os arquivos existentes não serão excluídos.  Você sempre pode salvar em arquivo sob demanda no menu de contexto.  
  
 Quando você salva dados do IntelliTrace para arquivo, você pode obter um arquivo. itrace para cada processo que o IntelliTrace coletado de.  Em seguida, você pode abrir o arquivo. itrace no Visual Studio, vá para**arquivo \/ abrir \/ arquivo**e selecionando o arquivo. itrace na caixa de diálogo Abrir arquivo.  Para obter mais informações, consulte[Depurar seu aplicativo usando dados salvos do IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
## Blogs  
 [IntelliTrace no Visual Studio Enterprise 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [Passo a passo do Live depurar usando o IntelliTrace no Visual Studio 2015 \(Editor de texto\)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [Passo a passo do Live depurar usando o IntelliTrace no Visual Studio 2015 \(Club Social\)](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [IntelliTrace no Visual Studio 2015 de Enterprise agora oferece suporte à anexação\!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [Coletar dados de um serviço do windows usando o IntelliTrace Standalone Collector](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [Editando o plano de coleta do IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [Personalizado TraceSource e depuração usando o IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Coletor autônomo do IntelliTrace e Pools de aplicativos executado sob contas do Active Directory](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## Fóruns  
 [Depurador do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## Vídeos  
 [IntelliTrace experiência](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Depuração de histórico com o IntelliTrace no Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)