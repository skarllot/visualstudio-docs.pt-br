---
title: "Usando o Microsoft Monitoring Agent | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usando o Microsoft Monitoring Agent
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode monitorar localmente aplicativos web em ASP.NET hospedados no IIS e o SharePoint 2010 ou 2013 aplicativos por erros, problemas de desempenho ou outros problemas usando **Microsoft Monitoring Agent**. Você pode salvar eventos de diagnóstico do agente em um arquivo de log \(. itrace\) do IntelliTrace. Você pode abrir o log no Visual Studio Enterprise \(mas não as edições Professional ou comunidade\) para depurar problemas com todas as ferramentas de diagnóstico de Visual Studio. Você também pode coletar dados de diagnóstico do IntelliTrace e método executando o agente em **rastreamento** modo. Agente de monitoramento da Microsoft podem ser integrado com [Application Insights](http://www.visualstudio.com/get-started/find-performance-problems-vs.aspx) e [do System Center Operations Manager](http://technet.microsoft.com/library/hh205987.aspx). Microsoft Monitoring Agent alterar o ambiente do sistema de destino quando ele está instalado.  
  
> [!NOTE]
>  Você também pode coletar dados de diagnóstico e método do IntelliTrace para web, SharePoint, WPF e aplicativos de formulário do Windows em computadores remotos sem alterar o ambiente de destino usando o **coletor autônomo do IntelliTrace**. O coletor autônomo tem um impacto de desempenho maior do que a execução do agente de monitoramento da Microsoft **Monitor** modo. Consulte [Usar o coletor autônomo do IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
 Se você usar o System Center 2012, use o Microsoft Monitoring Agent com o Operations Manager para receber alertas sobre problemas e criar itens de trabalho do Team Foundation Server com links para os logs do IntelliTrace salvos. Você pode atribuir esses itens de trabalho a outros usuários para uma depuração adicional. Consulte [integrando o Operations Manager aos processos de desenvolvimento](http://technet.microsoft.com/library/jj614609.aspx) e [Monitorando com Microsoft Monitoring Agent](http://technet.microsoft.com/en-us/library/dn465153.aspx).  
  
 Antes de começar, verifique se você tem o código\-fonte correspondente e os símbolos para o código compilado e implantado. Isso ajuda você a ir diretamente ao código do aplicativo ao iniciar a depuração e a navegação de eventos de diagnóstico no log do IntelliTrace.[Configure suas compilações](../debugger/diagnose-problems-after-deployment.md) para que o Visual Studio pode localizar e abrir o código\-fonte correspondente ao código implantado automaticamente.  
  
1.  [Etapa 1: Configurar o agente de monitoramento da Microsoft](#SetUpMonitoring)  
  
2.  [Etapa 2: Iniciar o monitoramento do aplicativo](#MonitorEvents)  
  
3.  [Etapa 3: Salvar eventos registrados](#SaveEvents)  
  
##  <a name="SetUpMonitoring"></a> Etapa 1: Configurar o agente de monitoramento da Microsoft  
 Configure o agente autônomo em seu servidor web para realizar o monitoramento local sem alterar o aplicativo. Se você usar o System Center 2012, consulte [instalar o agente de monitoramento da Microsoft](http://technet.microsoft.com/library/dn465156.aspx).  
  
###  <a name="SetUpStandaloneMMA"></a> Configurar o agente autônomo  
  
1.  Verifique se:  
  
    -   O servidor web está executando [suporte para versões do Internet Information Services \(IIS\)](http://technet.microsoft.com/en-us/library/dn465154.aspx).  
  
    -   O servidor web tem o .NET Framework 3.5, 4 ou 4.5.  
  
    -   O servidor web está executando o Windows PowerShell 3.0 ou posterior.[P: E se eu tiver o Windows PowerShell 2.0?](#PowerShell2)  
  
    -   Você tem permissões de administrador no servidor web para executar comandos do PowerShell e reciclar o pool de aplicativos quando você iniciar o monitoramento.  
  
    -   Você desinstalou alguma versão anterior do agente de monitoramento da Microsoft.  
  
2.  [Baixar o Microsoft Monitoring Agent gratuitamente](http://go.microsoft.com/fwlink/?LinkId=320384), qualquer versão de 32 bits do **MMASetup i386.exe** ou versão de 64 bits **MMASetup AMD64.exe**, da Microsoft Download Center em seu servidor web.  
  
3.  Execute o executável baixado para iniciar o Assistente de instalação.  
  
4.  Crie um diretório seguro em seu servidor web para armazenar os logs do IntelliTrace, por exemplo, **C:\\IntelliTraceLogs**.  
  
     Certifique\-se de criar esse diretório antes de você iniciar o monitoramento. Para evitar deixar seu aplicativo mais lento, escolha um local em um disco de alta velocidade local que não seja muito ativo.  
  
    > [!IMPORTANT]
    >  Logs do IntelliTrace podem conter dados pessoais e confidenciais. Restrinja esse diretório a apenas essas identidades que devem trabalhar com os arquivos. Verifique as políticas de privacidade da sua empresa.  
  
5.  Para executar o monitoramento detalhado e nível de função ou para monitorar aplicativos do SharePoint, dê o pool de aplicativos que hospeda sua web app ou aplicativo do SharePoint leitura e permissões de gravação para o diretório de log do IntelliTrace.[P: como configurar permissões para o pool de aplicativos?](#FullPermissionsITLog)  
  
### PERGUNTAS E RESPOSTAS  
  
####  <a name="PowerShell2"></a> P: E se eu tiver o Windows PowerShell 2.0?  
 **R:** é altamente recomendável que você use o PowerShell 3.0. Caso contrário, você precisará importar os cmdlets do Microsoft Monitoring Agent PowerShell sempre que executar o PowerShell. Além disso, você não terá acesso ao conteúdo de Ajuda que pode ser baixado.  
  
1.  Abra um **do Windows PowerShell** ou **o Windows PowerShell ISE** janela de prompt de comando como administrador.  
  
2.  Importe o módulo Microsoft Monitoring Agent PowerShell do local de instalação padrão:  
  
     **PS C:\>Import\-Module "C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\PowerShell\\Microsoft.MonitoringAgent.PowerShell\\Microsoft.MonitoringAgent.PowerShell.dll"**  
  
3.  [TechNet visite](http://technet.microsoft.com/systemcenter/default) para obter o conteúdo mais recente da Ajuda.  
  
####  <a name="FullPermissionsITLog"></a> P: como configurar permissões para o pool de aplicativos?  
 **R:** usar as janelas **icacls** de comando ou use Windows Explorer \(Explorador de arquivos\). Por exemplo:  
  
-   Para configurar as permissões com o Windows **icacls** comando:  
  
    -   Para um aplicativo web no **DefaultAppPool** pool de aplicativos:  
  
         `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool": RX`  
  
    -   Para um aplicativo SharePoint no **SharePoint \- 80** pool de aplicativos:  
  
         `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80": RX`  
  
     \- ou \-  
  
-   Para configurar permissões com o Windows Explorer \(ou Explorador de arquivos\):  
  
    1.  Abra **propriedades** para o diretório de log do IntelliTrace.  
  
    2.  Sobre o **segurança** guia, escolha **Editar**, **Add**.  
  
    3.  Verifique se **entidades de segurança internas** aparece no **Selecione este tipo de objeto** caixa. Se ele não estiver presente, escolha **tipos de objeto** para adicioná\-lo.  
  
    4.  Verifique se o computador local aparece no **deste local** caixa. Se ele não estiver presente, escolha **locais** para alterá\-lo.  
  
    5.  No **Digite os nomes de objeto a selecionar** caixa, adicione o pool de aplicativos para o aplicativo web ou aplicativo do SharePoint.  
  
    6.  Escolha **Verificar nomes** para resolver o nome. Clique em **OK**.  
  
    7.  Verifique se o pool de aplicativos tem **Ler & executar** permissões.  
  
##  <a name="MonitorEvents"></a> Etapa 2: Iniciar o monitoramento do aplicativo  
 Usar o Windows PowerShell [Start\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) comando para iniciar o monitoramento de seu aplicativo. Se você usar o System Center 2012, consulte [monitoramento de aplicativos Web com o Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
1.  No seu servidor web, abra um **do Windows PowerShell** ou **o Windows PowerShell ISE** janela de prompt de comando como administrador.  
  
     ![Open Windows PowerShell as administrator](../debugger/media/ffr_powershellrunadmin.png "FFR\_PowerShellRunAdmin")  
  
2.  Execute o [Start\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313686) comando para iniciar o monitoramento de seu aplicativo. Isso reiniciará todos os aplicativos web no servidor web.  
  
     Aqui está a sintaxe abreviada:  
  
     **Start\-WebApplicationMonitoring** *"\< appName \>"* *\< monitoringMode \>* *"\< outputPath \>"* *\< UInt32 \>* *"\< collectionPlanPathAndFileName \>"*  
  
     Aqui está um exemplo que usa apenas o nome do aplicativo web e leve **Monitor** modo:  
  
     **PS C:\\\>Start\-WebApplicationMonitoring "Fabrikam\\FabrikamFiber.Web" Monitor "C:\\IntelliTraceLogs"**  
  
     Aqui está um exemplo que usa o caminho do IIS e leve **Monitor** modo:  
  
     **PS C:\\\>Start\-WebApplicationMonitoring "IIS:\\sites\\Fabrikam\\FabrikamFiber.Web" Monitor "C:\\IntelliTraceLogs"**  
  
     Depois que você inicia o monitoramento, você poderá ver o Microsoft Monitoring Agent pausar enquanto seus aplicativos são reiniciados.  
  
     ![Start monitoring with MMA confirmation](../debugger/media/ffr_powershellstartmonitoringconfirmation.png "FFR\_PowerShellStartMonitoringConfirmation")  
  
    |||  
    |-|-|  
    |*"\< appName \>"*|Especifique o caminho para o nome do aplicativo web e sites no IIS. Você também pode incluir o caminho do IIS, se preferir.<br /><br /> *"\< IISWebsiteName \> \\ \< IISWebAppName \>"*<br /><br /> \- ou \-<br /><br /> **"IIS:\\sites** *\\ \< IISWebsiteName \> \\ \< IISWebAppName \> "*<br /><br /> Você pode encontrar esse caminho no Gerenciador do IIS. Por exemplo:<br /><br /> ![Path to IIS web site and web app](../debugger/media/ffr_iismanager.png "FFR\_IISManager")<br /><br /> Você também pode usar o [Get\-WebSite](http://technet.microsoft.com/library/ee807832.aspx) e [Get WebApplication](http://technet.microsoft.com/library/ee790554.aspx) comandos.|  
    |*\< monitoringMode \>*|Especifique o modo de monitoramento:<br /><br /> <ul><li>**Monitor**: Mínimo registre detalhes sobre eventos de desempenho e eventos de exceção. Esse modo usa o plano de coleta padrão.</li><li>**Trace**: Registrar detalhes no nível de função ou monitore o SharePoint 2010 e do SharePoint 2013 usando o plano de coleta especificado. Esse modo pode fazer seu aplicativo executado mais lentamente.<br /><br /> <ul><li>[P: como configurar permissões para o pool de aplicativos?](#FullPermissionsITLog)</li><li>[P: como obtenho o máximo de dados sem deixar meu aplicativo mais lento?](#Minimizing)</li></ul><br />     Este exemplo registra eventos de um aplicativo do SharePoint hospedado em um site do SharePoint:<br /><br />     **Start\-WebApplicationMonitoring "FabrikamSharePointSite\\FabrikamSharePointApp" Trace "C:\\Program Files\\Microsoft Monitoring Agent\\Agent\\IntelliTraceCollector\\collection\_plan.ASP.NET.default.xml" "C:\\IntelliTraceLogs"**</li><li>**Custom**: Registre detalhes personalizadas usando o plano de coleta personalizado especificado. Você precisará reiniciar o monitoramento se editar o plano de coleta depois monitoramento já tiver começado.</li></ul>|  
    |*"\< outputPath \>"*|Especifique o caminho completo do diretório para armazenar os logs do IntelliTrace. Certifique\-se de criar esse diretório antes de você iniciar o monitoramento.|  
    |*\< UInt32 \>*|Especifique o tamanho máximo para o log do IntelliTrace. O tamanho máximo padrão do log do IntelliTrace é 250 MB.<br /><br /> Quando o log atinge esse limite, o agent substitui as entradas mais antigas para liberar espaço para mais entradas. Para alterar esse limite, use o **\-MaximumFileSizeInMegabytes** opção ou editar o `MaximumLogFileSize` atributo no plano de coleta.|  
    |*"\< collectionPlanPathAndFileName \>"*|Especifique o caminho completo ou caminho relativo e o nome do arquivo do plano de coleta. Esse plano é um arquivo. XML que define as configurações para o agente.<br /><br /> Esses planos são incluídos no agente e trabalham com aplicativos web e aplicativos do SharePoint:<br /><br /> -   **collection\_plan.ASP.NET.default.XML**<br />     Coleta apenas eventos, como exceções, eventos de desempenho, chamadas de banco de dados e solicitações do servidor Web.<br />-   **collection\_plan.ASP.NET.Trace.XML**<br />     Coleta chamadas no nível da função mais todos os dados no plano de coleta padrão. Esse plano é bom para análise detalhada, mas talvez seu aplicativo mais lento.<br /><br /> Você pode encontrar versões localizadas desses planos nas subpastas do agente. Você também pode [personalizar esses planos ou criar seus próprios planos de](http://go.microsoft.com/fwlink/?LinkId=227871) para evitar deixar seu aplicativo mais lento. Coloque todos os planos personalizados no mesmo local seguro que o agente.<br /><br /> [P: como obtenho o máximo de dados sem deixar meu aplicativo mais lento?](#Minimizing)|  
  
     Para obter mais informações sobre a sintaxe completa e outros exemplos, execute o **get\-help Start\-WebApplicationMonitoring –detailed** comando ou o **get\-help Start\-WebApplicationMonitoring –examples** comando.  
  
3.  Para verificar o status de todos os aplicativos web monitorados, executados o [Get\-WebApplicationMonitoringStatus](http://go.microsoft.com/fwlink/?LinkID=313685) comando.  
  
### PERGUNTAS E RESPOSTAS  
  
####  <a name="Minimizing"></a> P: como obtenho o máximo de dados sem deixar meu aplicativo mais lento?  
 **R:** Microsoft Monitoring Agent pode coletar muitos dados e afeta o desempenho do seu aplicativo dependendo dos dados que você escolher para coletar e como coletá\-los. Aqui estão algumas maneiras de obter o máximo de dados sem deixar seu aplicativo mais lento:  
  
-   Para aplicativos web e aplicativos do SharePoint, o agente grava os dados para cada aplicativo que compartilha o pool de aplicativos especificado. Isso pode retardar qualquer aplicativo que compartilha o mesmo pool de aplicativos, embora você possa restringir a coleta aos módulos de um único aplicativo. Para evitar a lentidão de outros aplicativos, hospede cada aplicativo em seu próprio pool de aplicativos.  
  
-   Examine os eventos para os quais o agente coleta dados no plano de coleta. Edite o plano de coleta para desabilitar eventos que não sejam relevantes ou não sejam interessantes. Isso pode melhorar o desempenho de inicialização e o desempenho de tempo de execução.  
  
     Para desabilitar um evento, defina a `enabled` de atributo para o `<DiagnosticEventSpecification>` elemento `false`:  
  
     `<DiagnosticEventSpecification enabled="false">`  
  
     Se o `enabled` atributo não existir, o evento está habilitado.  
  
     Por exemplo:  
  
    -   Desabilite eventos do fluxo de trabalho do Windows para aplicativos que não usam o fluxo de trabalho do Windows.  
  
    -   Desabilite eventos do registro para aplicativos que acessam o registro, mas não mostrem problemas com as configurações do registro.  
  
-   Examine os módulos para o qual o agente coleta dados no plano de coleta. Edite o plano de coleta para incluir somente os módulos que lhe interessam.  
  
     Isso reduz a quanta informação de chamada de método e outros dados de instrumentação que o agente coleta quando o aplicativo é iniciado e executado. Esses dados o ajuda a navegar pelo código quando você está depurando e examinando os valores passados e retornados de chamadas de função.  
  
    1.  Abra o plano de coleta. Encontre o `<ModuleList>` elemento.  
  
    2.  Em `<ModuleList>`, defina o `isExclusionList` atributo `false`.  
  
    3.  Use o `<Name>` elemento para especificar cada módulo com um dos seguintes: nome do arquivo, o valor de cadeia de caracteres para incluir qualquer módulo cujo nome contenha essa cadeia de caracteres ou chave pública.  
  
     Este exemplo cria uma lista que coleta dados somente do módulo principal do aplicativo web Fabrikam Fiber:  
  
    ```xml  
    <ModuleList isExclusionList="false"> <Name>FabrikamFiber.Web.dll</Name> </ModuleList>  
  
    ```  
  
     Para coletar dados de qualquer módulo cujo nome inclua "Fabrikam", crie uma lista como esta:  
  
    ```xml  
    <ModuleList isExclusionList="false"> <Name>Fabrikam</Name> </ModuleList>  
  
    ```  
  
     Para coletar dados de módulos especificando seus tokens de chave pública, crie uma lista como esta:  
  
    ```xml  
    <ModuleList isExclusionList="false"> <Name>PublicKeyToken:B77A5C561934E089</Name> <Name>PublicKeyToken:B03F5F7F11D50A3A</Name> <Name>PublicKeyToken:31BF3856AD364E35</Name> <Name>PublicKeyToken:89845DCD8080CC91</Name> <Name>PublicKeyToken:71E9BCE111E9429C</Name> </ModuleList>  
  
    ```  
  
     **P: por que não basta excluir módulos em vez disso?**  
  
     **R:** por padrão, os planos de coleta excluem módulos definindo o `isExclusionList` atributo `true`. No entanto, isso ainda pode coletar dados de módulos que não atendem aos critérios da lista ou que não interessem a você, como módulos de terceiros ou de código\-fonte aberto.  
  
#### P: quais valores faz o agente coleta?  
 **R:** para reduzir o impacto no desempenho, o agente coleta apenas estes valores:  
  
-   Tipos de dados primitivos que são passados e retornados de métodos  
  
-   Tipos de dados primitivos em campos para objetos de nível superior passados e retornados de métodos  
  
 Por exemplo, suponha que você tenha um `AlterEmployee` assinatura do método que aceita um inteiro `id` e uma `Employee` objeto `oldemployee`:  
  
 `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
 O `Employee` tipo tem os seguintes atributos: `Id`, `Name`, e `HomeAddress`. Existe uma relação de associação entre `Employee` e `Address` tipo.  
  
 ![Relação entre o funcionário e o endereço](~/debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
 O agente grava os valores para `id`, `Employee.Id`, `Employee.Name` e o `Employee` objeto retornado do `AlterEmployee` método. No entanto, o agente não registra informações sobre o `Address` objeto diferente se ele era nulo ou não. O agente não registra dados sobre variáveis locais no `AlterEmployee` método, a menos que outros métodos usem essas variáveis locais como parâmetros no ponto em que eles são gravados como parâmetros de método.  
  
##  <a name="SaveEvents"></a> Etapa 3: Salvar eventos registrados  
 Quando você encontrar um erro ou um problema de desempenho, salve os eventos registrados em um log do IntelliTrace. O agente cria o log apenas se tiver registrado eventos. Se você usar o System Center 2012, consulte [monitoramento de aplicativos Web com o Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465157.aspx).  
  
### Salvar eventos registrados, mas continuar monitorando  
 Quando você deseja criar o log do IntelliTrace, mas não quiser reiniciar o aplicativo ou parar de monitorar, siga estas etapas. O agente continua o monitoramento, mesmo que o servidor ou o aplicativo for reiniciado.  
  
1.  No seu servidor web, abra uma janela de prompt de comando do Windows PowerShell como administrador.  
  
2.  Execute o [Checkpoint\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313684) comando para salvar um instantâneo do log do IntelliTrace:  
  
     **Checkpoint\-WebApplicationMonitoring** *"\< IISWebsiteName \> \\ \< IISWebAppName \>"*  
  
     \- ou \-  
  
     **Checkpoint\-WebApplicationMonitoring "IIS:\\sites** *\\ \< IISWebsiteName \> \\ \< IISWebAppName \> "*  
  
     Por exemplo:  
  
     **PS C:\\\>Checkpoint\-WebApplicationMonitoring "Fabrikam\\FabrikamFiber.Web"**  
  
     \- ou \-  
  
     **PS C:\\\>Checkpoint\-WebApplicationMonitoring "IIS:\\sites\\Fabrikam\\FabrikamFiber.Web"**  
  
     Para obter mais informações, execute o **get\-help Checkpoint\-WebApplicationMonitoring –detailed** comando ou o **get\-help Checkpoint\-WebApplicationMonitoring –examples** comando.  
  
3.  Copiar o log para uma pasta compartilhada segura e, em seguida, abra o log em um computador que tenha o Visual Studio Enterprise \(mas não as edições Professional ou comunidade\).  
  
    > [!IMPORTANT]
    >  Tome cuidado ao compartilhar logs do IntelliTrace porque eles podem conter dados pessoais e confidenciais. Verifique se a pessoa que pode acessar esses logs tem permissões para analisar os dados. Verifique as políticas de privacidade da sua empresa.  
  
 **Próximo:** [Diagnose registrou eventos no Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
### Salvar eventos registrados e parar monitoramento  
 Siga estas etapas quando você apenas deseja obter informações de diagnóstico durante a reprodução de um problema específico. Isso reiniciará todos os aplicativos web no servidor web.  
  
1.  No seu servidor web, abra uma janela de prompt de comando do Windows PowerShell como administrador.  
  
2.  Execute o [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) comando para criar o log do IntelliTrace e parar de monitorar um aplicativo web específico:  
  
     **Stop\-WebApplicationMonitoring** *"\< IISWebsiteName \> \\ \< IISWebAppName \>"*  
  
     \- ou \-  
  
     **Stop\-WebApplicationMonitoring "IIS:\\sites** *\\ \< IISWebsiteName \> \\ \< IISWebAppName \> "*  
  
     Ou parar de monitorar todos os aplicativos da web:  
  
     **Stop\-WebApplicationMonitoring \-All**  
  
     Por exemplo:  
  
     **PS C:\\\>Stop\-WebApplicationMonitoring "Fabrikam\\iFabrikamFiber.Web"**  
  
     \- ou \-  
  
     **PS C:\\\>Stop\-WebApplicationMonitoring "IIS:\\sites\\Fabrikam\\FabrikamFiber.Web"**  
  
     Para obter mais informações, execute o **get\-help Stop\-WebApplicationMonitoring –detailed** comando ou o **get\-help Stop\-WebApplicationMonitoring –examples** comando.  
  
3.  Copiar o log para uma pasta compartilhada segura e, em seguida, abra o log em um computador que tenha o Visual Studio Enterprise.  
  
 **Próximo:** [Diagnose registrou eventos no Visual Studio Enterprise](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
## PERGUNTAS E RESPOSTAS  
  
### P: onde posso obter mais informações?  
  
#### Blogs  
 [Apresentando o Microsoft Monitoring Agent](http://blogs.msdn.com/b/visualstudioalm/archive/2013/09/20/introducing-microsoft-monitoring-agent.aspx)  
  
 [Otimizando a coleta do IntelliTrace em servidores de produção](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
#### Fóruns  
 [Diagnóstico do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)