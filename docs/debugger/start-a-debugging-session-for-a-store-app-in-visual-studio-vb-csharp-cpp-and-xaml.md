---
title: "Iniciar uma sess&#227;o de depura&#231;&#227;o de um aplicativo da Store no Visual Studio (VB, C#, C++ e XAML) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.IVCAppHostRemoteDebugPageObject.MachineName"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType"
  - "ImmersiveProjects.Properties.Debug"
  - "VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication"
  - "VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback"
  - "AppPackage.Properties.Debug"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.Authentication"
  - "VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Iniciar uma sess&#227;o de depura&#231;&#227;o de um aplicativo da Store no Visual Studio (VB, C#, C++ e XAML)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows and Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Este tópico descreve como iniciar uma sessão de depuração para aplicativos da Windows Store escritos em XAML e Visual C\+\+, Visual C\# ou Visual Basic. Depurar um aplicativo envolve configurar a sessão de depuração e escolher a maneira de iniciar o aplicativo.  
  
> [!NOTE]
>  Para aplicativos escritos em JavaScript e HTML, veja [Iniciar uma sessão de depuração \(JavaScript\)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [A maneira fácil de iniciar a depuração](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurar a sessão de depuração](#BKMK_Configure_the_debugging_session)  
  
-   [Abrir a página de propriedades de depuração do projeto](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Escolher as opções de configuração de compilação](#BKMK_Choose_the_build_configuration_options)  
  
-   [Escolher o destino de implantação](#BKMK_Choose_the_deployment_target)  
  
-   [Escolher o depurador a ser usado](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Opcional) Atrasar o início da sessão de depuração](#BKMK__Optional__Delay_starting_the_debug_session)  
  
-   [(Opcional) Desabilitar loopbacks de rede](#BKMK__Optional__Disable_network_loopbacks)  
  
-   [(Opcional) Reinstalar o aplicativo ao iniciar a depuração](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)  
  
-   [(Opcional) Desativar a requisição de autenticação para iniciar o depurador remoto](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)  
  
 [Iniciar a sessão de depuração](#BKMK_Start_the_debugging_session)  
  
-   [Iniciar a depuração (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Iniciar a depuração (F5), mas atrasar o início do aplicativo](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
-   [Iniciar um aplicativo instalado no depurador](#BKMK_Start_an_installed_app_in_the_debugger)  
  
-   [Anexar o depurador a um aplicativo em execução](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
    -   [Definir o aplicativo para ser executado no modo de depuração](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
    -   [Anexar o depurador](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> A maneira fácil de iniciar a depuração  
  
1.  Abra a solução do aplicativo no Visual Studio.  
  
2.  Escolha F5.  
  
 O Visual Studio compila e inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim. Para obter mais informações, consulte [Navegar por uma sessão de depuração \(Xaml e c\#\)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> Configurar a sessão de depuração  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Abrir a página de propriedades de depuração do projeto  
  
1.  No Gerenciador de Soluções, selecione o projeto. No menu de atalho, escolha **Propriedades**.  
  
2.  Faça isso para abrir a página de propriedades de depuração do projeto:  
  
    -   Para aplicativos em Visual C\# e Visual Basic, escolha **Depurar**.  
  
         ![C&#35; &#47; VB project debug property page](../debugger/media/dbg_csvb_debugpropertypage.png "DBG\_CsVb\_DebugPropertyPage")  
  
    -   Para aplicativos em Visual C\+\+, expanda o nó **Propriedades de Configuração** e escolha **Depuração**.  
  
         ![C&#43;&#43; Windows Store app debugging property page](../debugger/media/dbg_cpp_debugpropertypage.png "DBG\_CPP\_DebugPropertyPage")  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> Escolher as opções de configuração de compilação  
  
1.  Na lista **Configuração**, escolha **Depurar** ou **\(Ativo\) Depurar**.  
  
2.  Na lista **Plataforma**, escolha a plataforma de destino da compilação. Na maioria dos casos, **Qualquer CPU** \(**Todas as Plataformas** no Visual C\+\+\) é a melhor opção.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Escolher o destino de implantação  
 ![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Você pode implantar e depurar um aplicativo da Windows Store no computador com Visual Studio, no simulador do Visual Studio no computador local ou em um dispositivo remoto.  
  
-   Para aplicativos do C\# e Visual Basic, escolha o destino na lista **Dispositivo de destino** na página de propriedades **Depurar** do projeto.  
  
-   Para aplicativos do C\+\+, escolha o destino na lista **Depurador a iniciar** na página de propriedades **Depuração**:  
  
 Escolha uma destas opções:  
  
|||  
|-|-|  
|**Computador Local**|Depura o aplicativo na sessão atual no computador local. Consulte [Executar aplicativos da Windows Store na máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [Executar aplicativos da Windows Store no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computador Remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [Executar aplicativos da Windows Store em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Se você escolher **Computador Remoto**, especifique o nome ou endereço IP do computador remoto de uma destas formas:  
  
-   Digite o nome ou endereço IP do computador remoto.  
  
    -   Para aplicativos em C\# e Visual Basic, digite o nome ou endereço IP na caixa **Máquina remota**.  
  
    -   Para aplicativos em C\+\+, digite o nome ou endereço IP na caixa **Nome do Computador**.  
  
-   Escolha o computador remoto na caixa de diálogo **Selecionar Conexão de Depurador Remoto**.  
  
     Para abrir a caixa de diálogo:  
  
    -   Para aplicativos em C\# e Visual Basic, escolha **Localizar**.  
  
    -   Para aplicativos em C\+\+, escolha a seta para baixo da caixa **Nome do Computador** e escolha **\<Localizar...\>**.  
  
     ![Marque a caixa de diálogo conexão de depurador remoto](~/debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  A caixa de diálogo **Selecionar Conexão de Depurador Remoto** exibe os computadores que estão na sub\-rede local e os computadores que estão diretamente conectados ao computador com o Visual Studio por um cabo Ethernet. Para especificar outro computador, digite o nome na caixa **Nome do Computador**.  
  
 ![Applies to Windows Phone only](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Você pode implantar e depurar um aplicativo da Windows Phone Store em um dispositivo ou em um dos emuladores de telefone do Visual Studio. Escolha o dispositivo ou emulador da lista **Dispositivo de destino**.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> Escolher o depurador a ser usado  
 Por padrão, o Visual Studio depura o código gerenciado nos aplicativos em C\# e Visual Basic.  
  
 Para aplicativos em C\# e Visual Basic, você pode optar por depurar o código gerenciado e o código C\/C\+\+ nativo. Marque a caixa de seleção **Habilitar depuração de código não gerenciado** para incluir o código nativo na sessão de depuração.  
  
 Por padrão, o Visual Studio depura o código nativo no aplicativo em C\+\+.  
  
 Para aplicativos em C\+\+, você pode escolher depurar tipos específicos de código que estão em componentes do seu aplicativo em vez do código nativo ou além dele. Especifique o código a ser depurado na lista **Tipo de Depurador** na página de propriedades **Depuração** do projeto do aplicativo.  
  
 Escolha um destes depuradores da lista **Processo do aplicativo**:  
  
|||  
|-|-|  
|**Somente Script**|Depura o código JavaScript no aplicativo. O código gerenciado e o código nativo são ignorados.|  
|**Somente Nativo**|Depura o código C\/C\+\+ nativo no aplicativo. O código gerenciado e o código JavaScript são ignorados.|  
|**Somente Gerenciado**|Depura o código gerenciado no aplicativo. O código JavaScript e o código C\/C\+\+ nativo são ignorados.|  
|**Misto \(Gerenciado e Nativo\)**|Depura o código C\/C\+\+ nativo e o código gerenciado no aplicativo. O código JavaScript é ignorado.|  
|**Somente GPU**|Depurar o código C\+\+ nativo que é executado em uma GPU \(unidade de processamento gráfico\).|  
  
 ![Applies to Windows Phone only](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 Para aplicativos de telefone da Windows Store, você também pode escolher o depurador a ser usado para os processos em segundo plano a partir de **Processo de tarefas em segundo plano**.  
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a> \(Opcional\) Atrasar o início da sessão de depuração  
 Por padrão, o Visual Studio inicia o aplicativo imediatamente quando você começa a depuração. Você também pode iniciar uma sessão de depuração, mas atrasar o início do seu aplicativo. Quando você escolhe essa opção, o aplicativo é iniciado no depurador quando é executado na tela inicial ou por um contrato de ativação ou quando é iniciado por outro processo ou método. Você também atrasa o início do aplicativo quando deseja depurar uma tarefa em segundo plano quando o aplicativo em si não está em execução.  
  
 Para atrasar a inicialização do aplicativo, você pode fazer o seguinte:  
  
-   Para aplicativos do Visual C\# e Visual Basic, selecione **Não iniciar, mas sim depurar meu código quando iniciar** na página de propriedades **Depurar**.  
  
-   Para aplicativos do Visual C\+\+, escolha **Sim** na lista **Iniciar Aplicativo** na página de propriedades **Depuração**.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> \(Opcional\) Desabilitar loopbacks de rede  
 ![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Por motivos de segurança, um aplicativo da Windows Store instalado da maneira padrão não pode efetuar chamadas de rede para o dispositivo em que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para o Windows Store, você deve testá\-lo sem a isenção.  
  
 Para remover a isenção de loopback de rede:  
  
-   Para aplicativos do Visual C\# e Visual Basic, desmarque a caixa de seleção **Permitir Loopback de Rede** na página de propriedades **Depurar**.  
  
-   Para aplicativos do Visual C\+\+, escolha **Não** na lista **Permitir Loopback de Rede** na página de propriedades **Depuração**.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a> \(Opcional\) Reinstalar o aplicativo ao iniciar a depuração  
 Para diagnosticar problemas com a instalação e configuração inicial do seu aplicativo do Visual C\# ou Visual Basic, escolha **Desinstalar e reinstalar meu pacote** na página de propriedades **Depurar** para recriar uma instalação original ao iniciar a depuração. Essa opção não está disponível para projetos do Visual C\+\+.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a> \(Opcional\) Desativar a requisição de autenticação para iniciar o depurador remoto  
 ![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Por padrão, você deve fornecer credenciais para executar o depurador remoto.  
  
> [!IMPORTANT]
>  Você também pode optar por executar o depurador remoto no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo não há nenhuma segurança de rede. Escolha o Modo Sem Autenticação somente se você tiver certeza de que a rede não corre risco de tráfego mal\-intencionado ou hostil.  
  
 Para remover a requisição de autenticação:  
  
1.  Para aplicativos Visual C\# e Visual Basic, desmarque a caixa de seleção **Usar Autenticação** na página de propriedades **Depurar**.  
  
2.  Para aplicativos Visual C\+\+, escolha **Não** na lista **Requer Autenticação** na página de propriedades **Depuração**.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Iniciar a sessão de depuração  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Iniciar a depuração \(F5\)  
 Quando você escolhe **Iniciar depuração** \(teclado: F5\) sobre o **Depurar** menu, o Visual Studio inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção ou o aplicativo chegue ao fim.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Iniciar a depuração \(F5\), mas atrasar o início do aplicativo  
 Você pode definir que o aplicativo seja executado no modo de depuração, mas inicie\-o por outro método que não seja o depurador. Por exemplo, convém depurar a inicialização do aplicativo no menu Iniciar ou depurar um processo em segundo plano do aplicativo sem iniciá\-lo. Para atrasar o início do aplicativo, faça o seguinte:  
  
-   Na página de propriedades **Depuração** do aplicativo \(**Depurar** em Visual C\+\+\):  
  
    -   Para aplicativos em Visual C\# e Visual Basic, escolha **Não iniciar, mas depurar meu código quando ele começar**.  
  
    -   Para aplicativos em Visual C\+\+, escolha **Sim** na lista **Iniciar Aplicativo**.  
  
-   Escolha **Iniciar depuração** sobre o **Depurar** menu \(teclado: F5\).  
  
-   Inicie o aplicativo pelo menu Iniciar, por um contrato de execução ou por outro procedimento.  
  
 O aplicativo é iniciado no modo de depuração. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
 . Para obter mais informações sobre como depurar tarefas em segundo plano, consulte [Disparar eventos de suspensão, retomada e segundo plano para a Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Iniciar um aplicativo instalado no depurador  
 Quando você inicia a depuração usando F5, o Visual Studio compila e implanta o aplicativo, define que ele seja executado no modo de depuração e, em seguida, inicia\-o. Para iniciar um aplicativo que já está instalado em um dispositivo, use a caixa de diálogo Depurar Pacote do Aplicativo Instalado. Esse procedimento é útil quando você precisa depurar um aplicativo instalado da Windows Store ou quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para o aplicativo. Por exemplo, você pode ter um sistema de compilação personalizado que não use projetos ou soluções do Visual Studio.  
  
 O aplicativo pode ser instalado no dispositivo local ou pode estar localizado em um dispositivo remoto.  É possível iniciar o aplicativo imediatamente ou defini\-lo para ser executado no depurador quando for iniciado por outro processo ou método, por exemplo, no menu Iniciar ou por um contrato de ativação. Você também pode definir o aplicativo para ser executado no modo de depuração quando quiser depurar um processo em segundo plano sem iniciar o aplicativo. Para obter mais informações, consulte [Disparar eventos de suspensão, retomada e segundo plano para a Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Para definir um aplicativo instalado para ser executado no modo de depuração, faça o seguinte:  
  
> [!NOTE]
>  O aplicativo não deve estar em execução quando você iniciar este procedimento.  
  
1.  No menu **Depurar**, escolha **Depurar Pacote do Aplicativo Instalado**.  
  
2.  Escolha uma destas opções na lista:  
  
    |||  
    |-|-|  
    |**Computador Local**|Depura o aplicativo na sessão atual no computador local. Consulte [Executar aplicativos da Windows Store na máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [Executar aplicativos da Windows Store no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Computador Remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [Executar aplicativos da Windows Store em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Escolha o aplicativo na lista **Pacotes do Aplicativo Instalados**.  
  
4.  Escolha o mecanismo de depuração a ser usado na lista **Depurar este tipo de código**.  
  
5.  \(Opcional\). Escolha **Não iniciar, mas sim depurar meu código quando iniciar** para depurar o aplicativo quando ele for iniciado por outro método ou para depurar um processo em segundo plano.  
  
 Quando você clicar em **Iniciar**, o aplicativo será iniciado ou definido para ser executado no modo de depuração.  
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Anexar o depurador a um aplicativo em execução  
 Para anexar o depurador a um aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], você deve usar o Gerenciador de Pacotes Depuráveis para definir a execução do aplicativo no modo de depuração. Esse recurso é instalado com as Ferramentas Remotas do Visual Studio.  
  
 Anexar o depurador a um aplicativo é útil quando você precisa depurar um aplicativo já instalado; por exemplo, um que tenha sido instalado da [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. A anexação é necessária quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para ele. Por exemplo, você pode ter um sistema de compilação personalizado que não use projetos ou soluções do Visual Studio.  
  
 Para anexar o depurador a um aplicativo, são necessárias as seguintes etapas:  
  
1.  Defina o aplicativo para ser executado no modo de depuração. Isso deve ser feito quando o aplicativo não está em execução.  
  
2.  Inicie o aplicativo. Você pode fazer isso pela tela inicial, por um contrato de execução ou por outro método.  
  
3.  Anexe o depurador ao aplicativo em execução.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Definir o aplicativo para ser executado no modo de depuração  
  
1.  Instale as Ferramentas Remotas do Visual Studio no dispositivo em que o aplicativo está instalado. Consulte [Instalando as ferramentas remotas](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  Na tela inicial, procure por `Debuggable Package Manager` e inicie\-o.  
  
     É exibida uma janela do PowerShell corretamente configurada para o cmdlet AppxDebug.  
  
3.  Para habilitar a depuração de um aplicativo, é preciso especificar o identificador NomeCompletodoPacote do aplicativo. Para ver uma lista de todos os aplicativos que incluem o NomeCompletodoPacote, digite `Get-AppxPackage` no aviso do PowerShell.  
  
4.  No prompt do PowerShell, digite `Enable-AppxDebug` *PackageFullName* em que o *PackageFullName* é o identificador PackageFullName do aplicativo.  
  
####  <a name="BKMK_Attach_the_debugger"></a> Anexar o depurador  
 Para anexar o depurador:  
  
1.  No menu **Depurar**, escolha **Anexar ao Processo**.  
  
     É exibida a caixa de diálogo **Anexar ao Processo**.  
  
2.  Para anexar a um aplicativo em um dispositivo remoto, especifique o dispositivo remoto na caixa **Qualificador**. Você pode:  
  
    -   Digitar o nome na caixa **Qualificador**.  
  
    -   Clicar na seta para baixo na caixa **Qualificador** e escolher um item em uma lista de dispositivos aos quais o depurador já foi anexado.  
  
    -   Escolher **Localizar** para selecionar o dispositivo em uma lista na sub\-rede local.  
  
3.  Especifique o tipo de código que você deseja depurar na caixa **Anexar a**.  
  
     Escolha **Selecionar** e siga um destes procedimentos:  
  
    -   Escolha **Determinar automaticamente o tipo de código a ser depurado**.  
  
    -   Escolha **Depurar esses tipos de código** e selecione um ou mais tipos na lista.  
  
4.  Na lista **Processos Disponíveis**, escolha o processo do aplicativo.  
  
5.  Escolha **Anexar**.  
  
 O Visual Studio anexa o depurador ao processo. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
## Consulte também  
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Navegar por uma sessão de depuração \(Xaml e c\#\)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)