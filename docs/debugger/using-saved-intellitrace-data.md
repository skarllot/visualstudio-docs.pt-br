---
title: "Usando dados salvos do IntelliTrace | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.historicaldebug.norepro"
helpviewer_keywords: 
  - "arquivos iTrace"
  - "IntelliTrace, arquivos de log"
  - "Arquivos de log do IntelliTrace"
  - "arquivos .iTrace"
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
caps.latest.revision: 106
caps.handback.revision: 106
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usando dados salvos do IntelliTrace
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vá para pontos específicos da execução do aplicativo ao iniciar a depuração de um arquivo de log \(. itrace\) do IntelliTrace. Esse arquivo pode conter eventos de desempenho, exceções, threads, etapas de teste, módulos e outras informações do sistema que o IntelliTrace registra durante a execução do seu aplicativo.  
  
 Certifique\-se de que você tenha:  
  
-   Arquivos de origem correspondentes e arquivos de símbolo \(. PDB\) para o código do aplicativo. Caso contrário, o Visual Studio não pode resolver os locais de origem e mostra a mensagem "Símbolos não encontrados". Consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e [Diagnosticar problemas após a implantação](../debugger/diagnose-problems-after-deployment.md).  
  
-   Visual Studio Enterprise \(mas não no Professional ou comunidade edições\) em seu computador de desenvolvimento ou outro computador para abrir arquivos. itrace  
  
-   Um arquivo. itrace de uma destas fontes:  
  
    |**Código\-fonte**|**Consulte**|  
    |-----------------------|------------------|  
    |Uma sessão do IntelliTrace no Visual Studio Enterprise \(mas não Professional ou Community Edition\)|[Recursos do IntelliTrace](../debugger/intellitrace-features.md)|  
    |Uma sessão de teste no Microsoft Test Manager. Isso anexa um arquivo. itrace a um item de trabalho do Team Foundation Server.|[Coletar mais dados de diagnóstico em testes manuais](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests)|  
    |Microsoft Monitoring Agent, sozinho ou com o System Center 2012 R2 Operations Manager para o ASP.NET web apps e aplicativos do SharePoint em execução na implantação|-   [Diagnosticar problemas após a implantação](../debugger/diagnose-problems-after-deployment.md)<br />-   [Novidades do System Center 2012 R2 Operations Manager](http://technet.microsoft.com/library/dn249700.aspx)|  
  
##  <a name="GetStarted"></a> O que você deseja fazer?  
  
-   [Abrir um log do IntelliTrace](#Open)  
  
-   [Compreender o log do IntelliTrace](#Understand)  
  
-   [Iniciar a depuração de um log do IntelliTrace](#StartDebugging)  
  
##  <a name="Open"></a> Abrir um log do IntelliTrace  
 Em um computador com Visual Studio Enterprise, abra o arquivo. itrace.  
  
-   Duas vezes no arquivo. itrace fora do Visual Studio ou abra o arquivo de dentro do Visual Studio.  
  
     \- ou \-  
  
-   Se o arquivo. itrace estiver anexado a um item de trabalho do Team Foundation Server, siga estas etapas no item de trabalho:  
  
    -   Em **todos os Links**, localize o arquivo. itrace. Abri\-lo.  
  
         \- ou \-  
  
    -   Em **etapas de reprodução**, escolha o **IntelliTrace** link.  
  
> [!TIP]
>  Se você fechou o arquivo do IntelliTrace durante a depuração, poderá reabri\-lo facilmente. Vá para o **Depurar** menu, escolha **IntelliTrace**, **Mostrar resumo do Log**. Você também pode escolher **Mostrar resumo do Log** no **IntelliTrace** janela. Isso está disponível apenas durante a depuração com o IntelliTrace.  
  
##  <a name="Understand"></a> Compreender o log do IntelliTrace  
 Algumas das seções a seguir no arquivo. itrace aparecem somente se você tiver coletado dados de uma fonte específica, por exemplo, do Test Manager ou de aplicativos do SharePoint.  
  
|**Seção**|**Contém**|**Origem da coleção**|  
|---------------|----------------|---------------------------|  
|[Violações de desempenho](#Performance)|Eventos de desempenho com chamadas de função que excedem o limite configurado|Microsoft Monitoring Agent, sozinho ou com o System Center 2012 R2 Operations Manager para o ASP.NET web aplicativos hospedados no IIS|  
|[Dados de exceção](#ExceptionData)|Exceções, incluindo a pilha de chamadas completa para cada exceção|Todas as fontes|  
|[Análise](#Analysis)|SharePoint 2010 e o SharePoint 2013 apenas para aplicativos. Diagnostique eventos do IntelliTrace e do SharePoint, como eventos do depurador, eventos ULS, exceções sem tratamento e outros dados que o Microsoft Monitoring Agent registrou.|Microsoft Monitoring Agent, qualquer um sozinho ou com o System Center 2012 R2 Operations Manager|  
|[Informações do sistema](#SystemInfo)|Configurações e especificações do sistema host|Todas as fontes|  
|[Lista de threads](#ThreadsList)|Threads executados durante a coleta|Todas as fontes|  
|[Dados de teste](#TestData)|Etapas de teste e seus resultados de uma sessão de teste|Test Manager|  
|[Módulos](#Modules)|Módulos que o processo de destino carregou na ordem em que foram carregados.|Todas as fontes|  
  
 Eis algumas dicas para ajudá\-lo a encontrar informações em cada seção:  
  
-   Escolha um cabeçalho de coluna para classificar os dados.  
  
-   Use a caixa de pesquisa para filtrar os dados. Pesquisa de texto sem formatação funciona em todas as colunas, exceto as colunas de hora. Você também pode filtrar pesquisas para uma coluna específica com um filtro por coluna. Digite o nome da coluna sem espaços, dois\-pontos \(**:**\) e o valor de pesquisa. Seguido por um ponto e vírgula \(**;**\) para adicionar outro valor de coluna e de pesquisa.  
  
     Por exemplo, para localizar os eventos de desempenho que tenham a palavra "lento" no **Descrição** coluna, digite:  
  
     `Descrição: lento`  
  
##  <a name="StartDebugging"></a> Iniciar a depuração de um log do IntelliTrace  
  
###  <a name="Performance"></a> Violações de desempenho  
 Examine os eventos de desempenho que foram registrados para seu aplicativo. Você pode ocultar esses eventos não ocorrem com frequência.  
  
##### Para iniciar a depuração de um evento de desempenho  
  
1.  Em **violações de desempenho**, examine os eventos de desempenho gravados, seu tempo de execução total e outras informações de evento. Em seguida, aprofunde\-se os métodos que foram chamados durante um evento de desempenho específicos.  
  
     ![View performance event details](../debugger/media/ffr_itsummarypageperformance.png "FFR\_ITSummaryPagePerformance")  
  
     Você pode também clicar duas vezes o evento.  
  
2.  Na página do evento, revise os tempos de execução dessas chamadas. Localize uma chamada lenta na árvore de execução.  
  
     As chamadas mais lentas aparecem em sua própria seção quando você tem várias chamadas aninhadas ou de outra forma.  
  
3.  Expanda essa chamada para revisar qualquer aninhada chamadas e valores de parâmetro gravados nesse momento.  
  
     \(Teclado: para mostrar ou ocultar uma chamada aninhada, pressione o **seta para a direita** ou **seta para a esquerda** respectivamente. Para mostrar e ocultar valores de parâmetro para uma chamada aninhada, pressione o **espaço** chave.\)  
  
     Inicie a depuração da chamada.  
  
     ![Start debugging from method call](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR\_ITSummaryPagePerformanceMethodsCalled")  
  
     Você pode também clicar duas vezes a chamada ou pressione a **Enter** chave.  
  
     Se for o método no código do aplicativo, o Visual Studio irá para esse método.  
  
     ![Go to application code from performance event](~/docs/debugger/media/ffr_itsummarypageperformancegotocode.png "FFR\_ITSummaryPagePerformanceGoToCode")  
  
     Agora você pode revisar outros valores gravados, a pilha de chamadas, depurar seu código, ou use o **IntelliTrace** janela [Mover para trás ou para frente "no tempo" entre outros métodos](../debugger/intellitrace.md) que foram chamados durante esse evento de desempenho.  
  
###  <a name="ExceptionData"></a> Dados de exceção  
 Revise as exceções acionadas e que foram registradas para seu aplicativo. Você pode agrupar as exceções que têm o mesmo tipo e pilha de chamadas para que você veja apenas a exceção mais recente.  
  
##### Para iniciar a depuração de uma exceção  
  
1.  Em **dados de exceção**, examine os eventos de exceção gravados, seus tipos, mensagens, e quando as exceções aconteceram. Para se aprofundar no código, inicie a depuração do evento mais recente em um grupo de exceções.  
  
     ![Start debugging from exception event](../debugger/media/ffr_itsummarypageexception.png "FFR\_ITSummaryPageException")  
  
     Você pode também clicar duas vezes o evento. Se os eventos não são agrupados, escolha **depurar este evento**.  
  
     Se a exceção aconteceu no código do aplicativo, o Visual Studio vai para onde a exceção ocorreu.  
  
     ![Go to application code from an exception event](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR\_ITSummaryPageExceptionGoToCode")  
  
     Agora você pode revisar outros valores gravados, a pilha de chamadas, ou usar o **IntelliTrace** janela [Mover para trás ou para frente "no tempo" entre outros eventos gravados](../debugger/intellitrace.md), código relacionado e os valores gravados nesses momentos no tempo.  
  
    |**Column**|**Mostra a**|  
    |----------------|------------------|  
    |**Tipo**|Tipo .NET da exceção|  
    |**Mensagem mais recente** para exceções agrupadas ou **mensagem** para exceções não agrupadas|A mensagem fornecida pela exceção|  
    |**Contagem** para exceções agrupadas|O número de vezes que a exceção foi gerada|  
    |**ID do thread** para exceções não agrupadas|ID do thread que gerou a exceção|  
    |**Hora do evento mais recente** ou **hora do evento**|Carimbo de data \/ hora registrado quando a exceção foi gerada|  
    |**Pilha de chamadas**|Pilha de chamadas para uma exceção.<br /><br /> Para ver a pilha de chamadas, escolha uma exceção na lista. A pilha de chamadas aparece abaixo da lista de exceção.|  
  
###  <a name="Analysis"></a> Análise  
 Diagnosticar problemas com aplicativos do SharePoint 2010 e o SharePoint 2013 usando uma ID de correlação do SharePoint ou examine qualquer exceção sem tratamento encontrado Microsoft Monitoring Agent.  
  
-   Use uma ID de correlação do SharePoint para localizar sua solicitação da web correspondente e eventos. Escolha um evento e, em seguida, iniciar a depuração no ponto onde e quando o evento ocorreu.  
  
-   Se o Microsoft Monitoring Agent encontrou exceções sem tratamento, escolha uma exceção e inicie a depuração no ponto onde e quando a exceção ocorreu.  
  
##### Iniciar a depuração com uma ID de correlação do SharePoint  
  
1.  Copie a ID de correlação do SharePoint de sua origem.  
  
     Por exemplo:  
  
     ![ID de correlação IntelliTrace &#45; erro do SharePoint&#45;](~/docs/debugger/media/sharepointerror_intellitrace.png "SharePointError\_IntelliTrace")  
  
2.  Abra o arquivo. itrace e vá para **análise** e insira a ID de correlação do SharePoint para revisar a solicitação da web correspondente e os eventos registrados.  
  
     ![Log IntelliTrace &#45; ID de correlação Inserir SharePoint](~/docs/debugger/media/entersharepointcorrelationid.png "EnterSharePointCorrelationID")  
  
3.  Em **eventos de solicitação**, examine os eventos. A partir da parte superior, eventos aparecem na ordem em que eles ocorreram.  
  
    1.  Escolha um evento para ver seus detalhes.  
  
    2.  Escolha **Iniciar depuração** para iniciar a depuração no ponto em que o evento ocorreu.  
  
     ![Arquivo de log IntelliTrace &#45; solicitação do modo de exibição da web e eventos](~/docs/debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")  
  
 Você pode ver esses tipos de eventos do SharePoint com eventos do IntelliTrace:  
  
-   **Eventos de perfil de usuário**  
  
     Esses eventos ocorrem quando o SharePoint carrega um perfil de usuário e quando as propriedades de perfil de usuário são lidas ou alteradas.  
  
-   **Eventos de log ULS \(serviço\) unificada**  
  
     Microsoft Monitoring Agent registra um subconjunto de eventos do SharePoint ULS e destes campos:  
  
    |**Campo do IntelliTrace**|**Campo do ULS do SharePoint**|  
    |-------------------------------|------------------------------------|  
    |**ID**|**EventID**|  
    |**Nível**|**Nível**|  
    |**Id da categoria**|**Id da categoria**|  
    |**Categoria**|**Categoria**|  
    |**Área**|**Produto**|  
    |**Saída**|**Mensagem**|  
    |**Id de correlação**|**Id de correlação**|  
  
##### Iniciar a depuração de uma exceção sem tratamento  
  
1.  Escolha uma ID de correlação do SharePoint para uma exceção. Exceções são agrupadas por tipo e pilha de chamadas.  
  
2.  \(Opcional\) Expanda **pilha de chamadas** para ver a pilha de chamadas para um grupo de exceções.  
  
3.  Escolha **exceção da depuração** para iniciar a depuração no ponto onde e quando a exceção ocorreu.  
  
     ![Exceções não tratadas IntelliTrace log &#45; SharePoint](~/docs/debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions\_IntelliTrace")  
  
 Para obter instruções, consulte [Instruções passo a passo: depurando um aplicativo do SharePoint usando o IntelliTrace](../Topic/Walkthrough:%20Debugging%20a%20SharePoint%20Application%20by%20Using%20IntelliTrace.md). Para os tipos de dados que os registros de agente, consulte [Recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
###  <a name="ThreadsList"></a> Lista de threads  
 Examine os threads registrados executados no processo de destino. Você pode iniciar a depuração do primeiro evento válido do IntelliTrace em um thread selecionado.  
  
##### Para iniciar a depuração de um thread específico  
  
1.  Em **lista de Threads**, escolha um thread.  
  
2.  Na parte inferior da **lista de Threads**, escolha **Iniciar depuração**. Você também pode clicar duas vezes em um thread.  
  
     Para iniciar a depuração de onde o aplicativo começa, clique duas vezes em **Thread principal**. Consulte [Recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
 Dados de thread que o usuário cria podem ser mais úteis do que os threads que um servidor cria e gerencia para aplicativos Web hospedados no IIS.  
  
|**Column**|**Mostra a**|  
|----------------|------------------|  
|**ID**|Número de identificação de thread|  
|**Nome**|Nome do thread. Threads sem nome aparecem como "\< sem nome \>".|  
|**Hora de início**|O thread foi criado de tempo|  
|**Hora de término**|Tempo que o thread foi concluído|  
  
###  <a name="TestData"></a> Dados de teste  
 Examine os dados do IntelliTrace Test Manager registrou ao testar seu aplicativo.  
  
##### Para iniciar a depuração de uma etapa de teste específico  
  
1.  Expanda **grade de etapas de teste**. Escolha uma etapa de teste.  
  
2.  Na parte inferior da **grade de etapas de teste**, escolha **Iniciar depuração**. Você também pode clicar duas vezes em uma etapa de teste.  
  
     Isso inicia a depuração do primeiro evento válido do IntelliTrace após a etapa de teste selecionado.  
  
     Quando houver dados de teste, o IntelliTrace tentará resolver a compilação do Team Foundation Server associada que foi usada para executar o teste. Se a compilação for encontrada, os símbolos associados para o aplicativo são resolvidos automaticamente.  
  
|**Campo**|**Mostra a**|  
|---------------|------------------|  
|**Sessão de teste**|Sessões de teste que foram registradas. Normalmente, há apenas um. Esta lista está vazia se dados de teste foi criados usando um teste exploratório manual.|  
|**Caso de teste**|Casos de teste da sessão de teste selecionado. Esta lista está vazia se dados de teste foi criados usando um teste exploratório manual.|  
|**Grade de etapas de teste**|Etapas de teste que foram registradas com o resultado do teste de aprovação ou falha|  
  
###  <a name="SystemInfo"></a> Informações do sistema  
 Esta seção mostra detalhes sobre o sistema que hospedou o aplicativo, por exemplo, o hardware, o sistema operacional, informações específicas de processo e ambientais.  
  
###  <a name="Modules"></a> Módulos  
 Esta seção mostra os módulos carregado do processo de destino. Os módulos aparecem na ordem em que foram carregados.  
  
|**Column**|**Mostra a**|  
|----------------|------------------|  
|**Nome do Módulo**|Nome de arquivo do módulo|  
|**Caminho do Módulo**|Local onde o módulo foi carregado do disco|  
|**ID do módulo**|Identificador exclusivo do módulo que é específico da versão e contribui para os arquivos de símbolo \(PDB\) correspondentes. Consulte [Finding symbol \(.pdb\) files and source files](http://msdn.microsoft.com/pt-br/05384c85-d264-4e18-abaa-aa482ab25470).|  
  
### Onde posso obter mais informações?  
 [Usar o coletor autônomo do IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
 [Recursos do IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Coletar mais dados de diagnóstico em testes manuais](/devops-test-docs/test/collect-more-diagnostic-data-in-manual-tests)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
#### Fóruns  
 [Depurador do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
#### Diretrizes  
 [Teste para entrega contínua com o Visual Studio 2012 – capítulo 6: uma caixa de ferramentas de teste](http://go.microsoft.com/fwlink/?LinkID=255203)