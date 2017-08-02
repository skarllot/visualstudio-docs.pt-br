---
title: "Usar o coletor aut&#244;nomo do IntelliTrace | Microsoft Docs"
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
  - "vs.historicaldebug.collectdataoutsideVS"
helpviewer_keywords: 
  - "IntelliTrace, depuração de aplicativos em produção"
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
caps.latest.revision: 105
caps.handback.revision: 105
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usar o coletor aut&#244;nomo do IntelliTrace
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O **coletor autônomo do IntelliTrace** permite coletar dados de diagnóstico do IntelliTrace para seus aplicativos em servidores de produção ou em outros ambientes sem instalar o Visual Studio no computador de destino e sem alterar o ambiente do sistema de destino. O coletor autônomo do IntelliTrace funciona em aplicativos da web, SharePoint, Windows Forms e WPF. Quando você terminar a coleta de dados, exclua o coletor para desinstalá\-lo.  
  
 Assista IntelliTrace em ação: [coletar e analisar dados do IntelliTrace na produção para depuração \(vídeo do Channel 9\)](http://go.microsoft.com/fwlink/?LinkID=251851)  
  
> [!NOTE]
>  Você também pode coletar os mesmos dados do IntelliTrace para aplicativos web e do SharePoint em execução em máquinas remotas usando o **Microsoft Monitoring Agent** na **rastreamento** modo.  
>   
>  Você pode coletar eventos relacionados ao desempenho nos dados do IntelliTrace, executando o agente em **Monitor** modo.**Monitor** modo tem menos de um impacto de desempenho de **rastreamento** modo ou o **coletor autônomo do IntelliTrace**. Microsoft Monitoring Agent alterar o ambiente do sistema de destino quando ele está instalado. Consulte [Usando o Microsoft Monitoring Agent](../debugger/using-the-microsoft-monitoring-agent.md).  
  
 **Requisitos**  
  
-   .NET framework 3.5, 4 ou 4.5  
  
-   Visual Studio Enterprise \(mas não no Professional ou comunidade edições\) em um computador de desenvolvimento ou outro computador para abrir arquivos. itrace  
  
    > [!NOTE]
    >  Certifique\-se de salvar o símbolo de arquivos \(. PDB\). Para depurar com o IntelliTrace e percorrer o código, você deve ter a correspondência de arquivos de origem e arquivos de símbolo. Consulte [Diagnosticar problemas após a implantação](../debugger/diagnose-problems-after-deployment.md).  
  
 **Perguntas frequentes**  
  
-   [Quais aplicativos funcionam com o coletor?](#WhatApps)  
  
-   [Como faço para começar?](#GetStarted)  
  
-   [Como obter o máximo de dados sem deixar meu aplicativo mais lento?](#Minimizing)  
  
-   [Onde mais posso obter dados do IntelliTrace?](#WhereElse)  
  
##  <a name="WhatApps"></a> Quais aplicativos funcionam com o coletor?  
  
-   Aplicativos Web ASP.NET hospedados no Internet Information Services \(IIS\) versão 7.0, 7.5 e 8.0  
  
-   Aplicativos do SharePoint 2010 e o SharePoint 2013  
  
-   Aplicativos de formulários do Windows Presentation Foundation \(WPF\) e Windows.  
  
##  <a name="GetStarted"></a> Como faço para começar?  
  
1.  [Instalar o coletor](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)  
  
2.  [Configurar permissões para o diretório do coletor](#ConfigurePermissionsRunningCollector)  
  
3.  [Instalar os cmdlets do PowerShell do IntelliTrace para coletar dados para aplicativos da Web ou aplicativos do SharePoint](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)  
  
4.  [Configurar permissões para o diretório do arquivo. itrace](#BKMK_Create_and_Configure_a_Log_File_Directory)  
  
5.  [Coletar dados de um aplicativo Web ou aplicativo do SharePoint](#BKMK_Collect_Data_from_IIS_Application_Pools)  
  
     \- ou \-  
  
     [Coletar dados de um aplicativo gerenciado](#BKMK_Collect_Data_from_Executables)  
  
6.  [Abra o arquivo. itrace no Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Instalar o coletor  
  
1.  No servidor do aplicativo, crie o diretório do coletor, por exemplo: **C:\\IntelliTraceCollector**  
  
2.  Obter o coletor do Microsoft Download Center ou da pasta de instalação do Visual Studio 2103 atualização 3.[Coletor do IntelliTrace para Visual Studio 2013 atualização 4](https://www.microsoft.com/en-us/download/details.aspx?id=44909)::  
  
    -   **Centro de Download da Microsoft**:  
  
        1.  Ao lado de **IntelliTraceCollector.exe**, escolha **baixar**.  
  
        2.  Salve IntelliTraceCollector.exe para o diretório do coletor, por exemplo: **C:\\IntelliTraceCollector**  
  
        3.  Execute IntelliTraceCollector.exe. Isso extrai o arquivo IntelliTraceCollection.cab.  
  
         \- ou \-  
  
    -   **Pasta de instalação do visual Studio**:  
  
        1.  Copie IntelliTraceCollection.cab da pasta a seguir:  
  
             **..\\Microsoft Visual Studio 12.0\\Common7\\IDE\\CommonExtensions\\Microsoft\\IntelliTrace\\12.0.0**  
  
        2.  Colocar IntelliTraceCollection.cab no diretório do coletor, por exemplo: **C:\\IntelliTraceCollector**  
  
3.  Expanda IntelliTraceCollection.cab:  
  
    1.  No servidor do aplicativo, abra uma janela de prompt de comando como administrador.  
  
    2.  Navegue até o diretório do coletor, por exemplo: **C:\\IntelliTraceCollector**  
  
    3.  Use o **expand** comando, incluindo o período \(**.**\) no final, expandir IntelliTraceCollection.cab:  
  
         `Expanda /f:* IntelliTraceCollection.cab.`  
  
        > [!NOTE]
        >  O período \(**.**\) preserva as subpastas que contêm planos de coleta localizada.  
  
##  <a name="ConfigurePermissionsRunningCollector"></a> Configurar permissões para o diretório do coletor  
  
1.  No servidor do aplicativo, abra uma janela de prompt de comando como administrador.  
  
2.  Use o Windows **icacls** comando para dar ao servidor permissões completas de administrador para o diretório do coletor. Por exemplo:  
  
     `icacls /grant "C:\IntelliTraceCollector" "` *\< Domain\\AdministratorID \>* `": F`  
  
3.  Para coletar dados de um aplicativo Web ou aplicativo do SharePoint:  
  
    1.  Dê a pessoa que executará os cmdlets do PowerShell do IntelliTrace permissões completas para o diretório do coletor.  
  
         Por exemplo:  
  
         `icacls /grant "C:\IntelliTraceCollector" "` *\< domínio \\ id\_do\_usuário \>* `": F`  
  
    2.  Dê o pool de aplicativos para o aplicativo Web ou aplicativo do SharePoint permissões read e execute para o diretório do coletor.  
  
         Por exemplo:  
  
        -   Para um aplicativo Web no **DefaultAppPool** pool de aplicativos:  
  
             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool": RX`  
  
        -   Para um aplicativo SharePoint no **SharePoint \- 80** pool de aplicativos:  
  
             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80": RX`  
  
##  <a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a> Instalar os cmdlets do PowerShell do IntelliTrace para coletar dados para aplicativos da Web ou aplicativos do SharePoint  
  
1.  No servidor do aplicativo, certifique\-se de que o PowerShell está habilitado. Na maioria das versões do Windows Server, você pode adicionar esse recurso no **Gerenciador do servidor** ferramenta administrativa.  
  
     ![Adding PowerShell by using Server Manager](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE\_ServerManager\_AddPowerShell")  
  
2.  Instale os cmdlets do PowerShell do IntelliTrace.  
  
    1.  Abra uma janela de comando do PowerShell como administrador.  
  
        1.  Escolha **Iniciar**, **todos os programas**, **Acessórios**, **do Windows PowerShell**.  
  
        2.  Escolha uma das seguintes etapas:  
  
            -   Em sistemas operacionais de 64 bits, abra o menu de atalho para **do Windows PowerShell**. Escolha **Executar como administrador**.  
  
            -   Em sistemas operacionais de 32 bits, abra o menu de atalho para **do Windows PowerShell \(x86\)**. Escolha **Executar como administrador**.  
  
    2.  Na janela de comando do PowerShell, use o **Import\-Module** comando para importar **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll**.  
  
         Por exemplo:  
  
         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`  
  
##  <a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> Configurar permissões para o diretório do arquivo. itrace  
  
1.  No servidor do aplicativo, crie o diretório do arquivo. itrace, por exemplo: **C:\\IntelliTraceLogFiles**  
  
    > [!NOTE]
    >  -   Para evitar deixar seu aplicativo mais lento, escolha um local em um disco de alta velocidade local que não seja muito ativo.  
    > -   Você pode colocar arquivos. itrace e os arquivos do coletor no mesmo lugar. No entanto, se você tiver um aplicativo Web ou aplicativo do SharePoint, verifique se que o local está fora do diretório que hospeda o aplicativo.  
  
    > [!IMPORTANT]
    >  -   Restringir o diretório do arquivo. itrace apenas para essas identidades que devem trabalhar com o coletor. Um arquivo. itrace pode conter informações confidenciais, como dados de usuários, bancos de dados, outros locais de origem e cadeias de conexão porque o IntelliTrace poderá registrar nenhum dado que passe em parâmetros de método ou como valores de retorno.  
    > -   Certifique\-se de quem pode abrir arquivos. itrace tem autoridade para exibir dados confidenciais. Tenha cuidado ao compartilhamento de arquivos. itrace. Se outras pessoas devem ter acesso, copie os arquivos em um local compartilhado seguro.  
  
2.  Para um aplicativo Web ou aplicativo do SharePoint, dê o seu pool de aplicativos, permissões completas para o diretório do arquivo. itrace. Você pode usar o Windows **icacls** de comando ou use Windows Explorer \(Explorador de arquivos\).  
  
     Por exemplo:  
  
    -   Para configurar as permissões com o Windows **icacls** comando:  
  
        -   Para um aplicativo Web no **DefaultAppPool** pool de aplicativos:  
  
             `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool": F`  
  
        -   Para um aplicativo SharePoint no **SharePoint \- 80** pool de aplicativos:  
  
             `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80": F`  
  
         \- ou \-  
  
    -   Para configurar permissões com o Windows Explorer \(ou Explorador de arquivos\):  
  
        1.  Abra **propriedades** para o diretório do arquivo. itrace.  
  
        2.  Sobre o **segurança** guia, escolha **Editar**, **Add**.  
  
        3.  Certifique\-se de **entidades de segurança internas** aparece no **Selecione este tipo de objeto** caixa. Se ele não estiver presente, escolha **tipos de objeto** para adicioná\-lo.  
  
        4.  Verifique se o computador local aparece no **deste local** caixa. Se ele não estiver presente, escolha **locais** para alterá\-lo.  
  
        5.  No **Digite os nomes de objeto a selecionar** caixa, adicione o pool de aplicativos para o aplicativo Web ou aplicativo do SharePoint.  
  
        6.  Escolha **Verificar nomes** para resolver o nome. Clique em **OK**.  
  
        7.  Verifique se o pool de aplicativos tem **controle total**.  
  
##  <a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a> Coletar dados de um aplicativo Web ou aplicativo do SharePoint  
  
1.  Para iniciar a coleta de dados, abra uma janela de comando do PowerShell como administrador e execute este comando:  
  
     `Iniciar IntelliTraceCollection` `"`*\< ApplicationPool \>*`"` *\< PathToCollectionPlan \>* *\< FullPathToITraceFileDirectory \>*  
  
    > [!IMPORTANT]
    >  Depois de executar esse comando, digite **Y** para confirmar que você deseja iniciar a coleta de dados.  
  
     Por exemplo, para coletar dados de um aplicativo SharePoint no **SharePoint \- 80** pool de aplicativos:  
  
     `Início-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`  
  
    |||  
    |-|-|  
    |*ApplicationPool*|O nome do pool de aplicativos em que seu aplicativo é executado|  
    |*PathToCollectionPlan*|O caminho para um plano de coleta, um arquivo. XML que define as configurações para o coletor.<br /><br /> Você pode especificar um plano que vem com o coletor. Os planos a seguir funcionam para aplicativos Web e aplicativos do SharePoint:<br /><br /> -   collection\_plan.ASP.NET.default.XML<br />     Coleta apenas eventos do IntelliTrace e eventos do SharePoint, incluindo exceções, chamadas de banco de dados e solicitações do servidor Web.<br />-   collection\_plan.ASP.NET.Trace.XML<br />     Chamadas de função de coleta e todos os dados em collection\_plan.ASP.NET.default.xml. Esse plano é bom para análise detalhada, mas pode reduzir a velocidade seu aplicativo mais do que collection\_plan.ASP.NET.default.xml.<br /><br /> Para evitar deixar seu aplicativo mais lento, personalizar esses planos ou criar seu próprio plano. Para segurança, coloque todos os planos personalizados no mesmo local seguro que os arquivos do coletor. Consulte [criação e personalização de planos de coleta do IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) e [Como obtenho o máximo de dados sem deixar meu aplicativo mais lento?](#Minimizing) **Note:**  Por padrão, o tamanho máximo do arquivo. itrace é 100 MB. Quando o arquivo. itrace atinge esse limite, o coletor de exclui entradas mais antigas do arquivo para liberar espaço para as entradas mais recentes. Para alterar esse limite, edite o plano de coleta `MaximumLogFileSize` atributo. <br /><br /> *Onde posso encontrar versões localizadas desses planos de coleção?*<br /><br /> Você pode encontrar planos localizados em subpastas do coletor.|  
    |*FullPathToITraceFileDirectory*|O caminho completo para o diretório do arquivo. itrace. **Security Note:**  Forneça o caminho completo, não um caminho relativo.|  
  
     O coletor anexa ao pool de aplicativos e começa a coletar dados.  
  
     *Pode abrir o arquivo. itrace neste momento?* Não, o arquivo está bloqueado durante a coleta de dados.  
  
2.  Reproduza o problema.  
  
3.  Para obter um instantâneo do arquivo. itrace, use esta sintaxe:  
  
     `IntelliTraceCollection de ponto de verificação` `"`*\< ApplicationPool \>*`"`  
  
4.  Para verificar o status do conjunto, use esta sintaxe:  
  
     `Get-IntelliTraceCollectionStatus`  
  
5.  Para interromper a coleta de dados, use a seguinte sintaxe:  
  
     `Stop IntelliTraceCollection` `"`*\< ApplicationPool \>*`"`  
  
    > [!IMPORTANT]
    >  Depois de executar esse comando, digite **Y** para confirmar que você deseja interromper a coleta de dados. Caso contrário, o coletor pode continuar a coleta de dados, o iTrace arquivo permanecerá bloqueado ou o arquivo não pode conter dados úteis.  
  
6.  [Abra o arquivo. itrace no Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_Collect_Data_from_Executables"></a> Coletar dados de um aplicativo gerenciado  
  
1.  Para iniciar seu aplicativo e coletar dados ao mesmo tempo, use a seguinte sintaxe:  
  
     *\< FullPathToIntelliTraceCollectorExecutable \>* `\IntelliTraceSC.exe iniciar /cp:` *\< PathToCollectionPlan \>* `/f:`*\< FullPathToITraceFileDirectoryAndFileName \>* *\< PathToAppExecutableFileAndFileName \>*  
  
     Por exemplo, para coletar dados de um aplicativo chamado **MyApp**:  
  
     `/F:"C:\IntelliTraceLogFiles\MyApp.itrace C:\IntelliTraceCollector\IntelliTraceSC.exe iniciar /cp:"C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml"" "C:\MyApp\MyApp.exe"`  
  
    |||  
    |-|-|  
    |*FullPathToIntelliTraceCollectorExecutable*|O caminho completo para o coletor executável, IntelliTraceSC.exe|  
    |*PathToCollectionPlan*|O caminho para um plano de coleta, um arquivo. XML que define as configurações para o coletor.<br /><br /> Você pode especificar um plano que vem com o coletor. Os planos a seguir funcionam para aplicativos gerenciados:<br /><br /> -   collection\_plan.ASP.NET.default.XML<br />     Coleta apenas eventos do IntelliTrace, incluindo exceções, chamadas de banco de dados e solicitações do servidor Web.<br />-   collection\_plan.ASP.NET.Trace.XML<br />     Chamadas de função de coleta e todos os dados em collection\_plan.ASP.NET.default.xml. Esse plano é bom para análise detalhada, mas pode reduzir a velocidade seu aplicativo mais do que collection\_plan.ASP.NET.default.xml.<br /><br /> Para evitar deixar seu aplicativo mais lento, personalizar esses planos ou criar seu próprio plano. Para segurança, coloque todos os planos personalizados no mesmo local seguro que os arquivos do coletor. Consulte [criação e personalização de planos de coleta do IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871) e [Como obtenho o máximo de dados sem deixar meu aplicativo mais lento?](#Minimizing) **Note:**  Por padrão, o tamanho máximo do arquivo. itrace é 100 MB. Quando o arquivo. itrace atinge esse limite, o coletor de exclui entradas mais antigas do arquivo para liberar espaço para as entradas mais recentes. Para alterar esse limite, edite o plano de coleta `MaximumLogFileSize` atributo. <br /><br /> *Onde posso encontrar versões localizadas desses planos de coleção?*<br /><br /> Você pode encontrar planos localizados em subpastas do coletor.|  
    |*FullPathToITraceFileDirectoryAndFileName*|O caminho completo para o diretório do arquivo. itrace e o nome do arquivo. itrace com o **.itrace** extensão. **Security Note:**  Forneça o caminho completo, não um caminho relativo.|  
    |*PathToAppExecutableFileAndFileName*|O caminho e o nome do seu aplicativo gerenciado|  
  
2.  Interrompa a coleta de dados, saindo do aplicativo.  
  
3.  [Abra o arquivo. itrace no Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)  
  
##  <a name="BKMK_View_IntelliTrace_Log_Files"></a> Abra o arquivo. itrace no Visual Studio Enterprise  
  
> [!NOTE]
>  Para depurar com o IntelliTrace e percorrer o código, você deve ter a correspondência de arquivos de origem e arquivos de símbolo. Consulte [Diagnosticar problemas após a implantação](../debugger/diagnose-problems-after-deployment.md).  
  
1.  Mova o arquivo. itrace ou copiá\-lo para um computador com Visual Studio Enterprise \(mas não Professional ou Community Edition\).  
  
2.  Duas vezes no arquivo. itrace fora do Visual Studio ou abra o arquivo de dentro do Visual Studio.  
  
     O Visual Studio mostra a **Resumo do IntelliTrace** página. Na maioria das seções, você pode analisar eventos ou outros itens, escolha um item e iniciar a depuração com o IntelliTrace no ponto onde e quando um evento ocorreu. Consulte [Depurar seu aplicativo usando dados salvos do IntelliTrace](../debugger/using-saved-intellitrace-data.md).  
  
    > [!NOTE]
    >  Para depurar com o IntelliTrace e percorrer o código, você deve ter a correspondência de arquivos de origem e símbolo arquivos em seu computador de desenvolvimento. Consulte [Diagnosticar problemas após a implantação](../debugger/diagnose-problems-after-deployment.md).  
  
##  <a name="Minimizing"></a> Como obtenho o máximo de dados sem deixar meu aplicativo mais lento?  
 IntelliTrace pode coletar muitos dados, portanto o impacto no desempenho do aplicativo depende dos dados que o IntelliTrace coleta e o tipo de código para analisar. Consulte [Otimizando a coleta do IntelliTrace em servidores de produção](http://go.microsoft.com/fwlink/?LinkId=255233).  
  
 Aqui estão algumas maneiras de obter o máximo de dados sem deixar seu aplicativo mais lento:  
  
-   Execute o coletor somente quando você acha que há um problema, ou você pode reproduzir o problema.  
  
     Iniciar coleta, reproduza o problema e, em seguida, parar a coleta. Abra o arquivo. itrace no Visual Studio Enterprise e examinar os dados. Consulte [Abra o arquivo. itrace no Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files).  
  
-   Para aplicativos Web e aplicativos do SharePoint, o coletor de registros de dados para cada aplicativo que compartilha o pool de aplicativos especificado. Isso pode retardar qualquer aplicativo que compartilha o mesmo pool de aplicativos, mesmo que você só pode especificar módulos para um único aplicativo em um plano de coleta.  
  
     Para impedir que o coletor de lentidão em outros aplicativos, hospede cada aplicativo em seu próprio pool de aplicativos.  
  
-   Revise os eventos no plano de coleta para o qual o IntelliTrace coleta dados. Edite o plano de coleta para desabilitar eventos que não sejam relevantes ou não sejam interessantes.  
  
     Para desabilitar um evento, defina a `enabled` de atributo para o `<DiagnosticEventSpecification>` elemento `false`:  
  
     `<DiagnosticEventSpecification enabled="false">`  
  
     Se o `enabled` atributo não existir, o evento está habilitado.  
  
     *Como isso melhora o desempenho?*  
  
    -   Você pode reduzir o tempo de inicialização, desabilitando os eventos que não sejam relevantes para o aplicativo. Por exemplo, desabilite eventos do fluxo de trabalho do Windows para aplicativos que não usam o fluxo de trabalho do Windows.  
  
    -   Você pode melhorar o desempenho de inicialização e o tempo de execução, desabilitando os eventos do registro para aplicativos que acessam o registro, mas não mostrem problemas com as configurações do registro.  
  
-   Examine os módulos no plano de coleta para o qual o IntelliTrace coleta dados. Edite o plano de coleta para incluir somente os módulos que lhe interessam:  
  
    1.  Abra o plano de coleta. Encontre o `<ModuleList>` elemento.  
  
    2.  Em `<ModuleList>`, defina o `isExclusionList` atributo `false`.  
  
    3.  Use o `<Name>` elemento para especificar cada módulo com um dos seguintes: nome do arquivo, o valor de cadeia de caracteres para incluir qualquer módulo cujo nome contenha essa cadeia de caracteres ou chave pública.  
  
     Por exemplo, para coletar dados de apenas o módulo da Web principal do aplicativo da Fabrikam Fiber Web, crie uma lista como esta:  
  
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
  
     *Como isso melhora o desempenho?*  
  
     Isso reduz a quantidade de informações de chamada de método e outros dados de instrumentação que o IntelliTrace coleta quando o aplicativo é iniciado e executado. Esses dados permite que você:  
  
    -   Percorrer o código após a coleta de dados.  
  
    -   Examine os valores passados para e retornados de chamadas de função.  
  
     *Por que não excluir módulos em vez disso?*  
  
     Por padrão, os planos de coleta excluem módulos definindo o `isExclusionList` atributo `true`. No entanto, a exclusão dos módulos ainda pode resultar na coleta de dados de módulos que não atendem aos critérios da lista e não interessem a você, como módulos de terceiros ou de código\-fonte aberto.  
  
-   *Há quaisquer dados que o IntelliTrace não coleta?*  
  
     Sim, para reduzir o impacto no desempenho, o IntelliTrace restringe a coleta de dados para valores de tipos de dados primitivos passados para e retornados de métodos e valores de tipos de dados primitivos em campos em objetos de nível superior passados para e retornados de métodos.  
  
     Por exemplo, suponha que você tenha um `AlterEmployee` assinatura do método que aceita um inteiro `id` e uma `Employee` objeto `oldemployee`:  
  
     `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
     O `Employee` tipo tem os seguintes atributos: `Id`, `Name`, e `HomeAddress`. Existe uma relação de associação entre `Employee` e `Address` tipo.  
  
     ![Relação entre o funcionário e o endereço](~/debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
     O coletor registra valores de `id`, `Employee.Id`, `Employee.Name` e o `Employee` objeto retornado do `AlterEmployee` método. No entanto, o coletor não registra informações sobre o `Address` objeto diferente se ele era nulo ou não. O coletor não registra dados sobre variáveis locais no `AlterEmployee` método, a menos que outros métodos usem essas variáveis locais como parâmetros no ponto em que eles são gravados como parâmetros de método.  
  
##  <a name="WhereElse"></a> Onde mais posso obter dados do IntelliTrace?  
  
-   IntelliTrace depuração sessão no Visual Studio Enterprise, consulte [Recursos do IntelliTrace](../debugger/intellitrace-features.md).  
  
-   De uma sessão de teste no Microsoft Test Manager, consulte [como: coletar dados do IntelliTrace para ajudar a depurar problemas difíceis](../Topic/How%20to:%20Collect%20IntelliTrace%20Data%20to%20Help%20Debug%20Difficult%20Issues.md).  
  
## Onde posso obter mais informações?  
 [Depurar seu aplicativo usando dados salvos do IntelliTrace](../debugger/using-saved-intellitrace-data.md)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
### Blogs  
 [Usando o coletor autônomo do IntelliTrace remotamente](http://go.microsoft.com/fwlink/?LinkId=262277)  
  
 [Criar e personalizar planos de coleta do IntelliTrace](http://go.microsoft.com/fwlink/?LinkId=227871)  
  
 [Otimizando a coleta do IntelliTrace em servidores de produção](http://go.microsoft.com/fwlink/?LinkId=255233)  
  
 [Blog do TFS do Visual Studio ALM \+](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### Fóruns  
 [Depurador do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
### Vídeos  
 [Vídeo do Channel 9: coletando e analisando dados do IntelliTrace](http://go.microsoft.com/fwlink/?LinkID=251851)