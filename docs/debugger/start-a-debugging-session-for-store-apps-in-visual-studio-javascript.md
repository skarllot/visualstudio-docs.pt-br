---
title: "Iniciar uma sess&#227;o de depura&#231;&#227;o para aplicativos da Store no Visual Studio (JavaScript) | Microsoft Docs"
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
  - "vs.debug.installedapppackagelauncher"
  - "vs.debug.error.wwahost_scriptdebuggingdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Iniciar uma sess&#227;o de depura&#231;&#227;o para aplicativos da Store no Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows and Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Este tópico descreve como iniciar uma sessão de depuração para os aplicativos da Windows Store gravados em JavaScript e HTML5. Você pode iniciar a depuração com um único pressionamento de tecla ou configurar a sessão de depuração para cenários específicos e escolher a maneira de iniciar o aplicativo.  
  
> [!NOTE]
>  Para aplicativos escritos em XAML e Visual C\#, Visual C\+\+ ou Visual Basic, consulte [Iniciar uma sessão de depuração \(VB, C\#, C\+\+ e XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [Neste tópico](#BKMK_In_this_topic)  
  
 [A maneira fácil de iniciar a depuração](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurar a sessão de depuração](#BKMK_Configure_the_debugging_session)  
  
-   [Abrir a página de propriedades de depuração do projeto](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Escolher as opções de configuração de compilação](#BKMK_Choose_the_build_configuration_options)  
  
-   [Escolher o destino de implantação](#BKMK_Choose_the_deployment_target)  
  
-   [Escolher o depurador a ser usado](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Opcional) Atrasar o início do aplicativo na sessão de depuração](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  
  
-   [(Opcional) Desabilitar loopbacks de rede](#BKMK__Optional__Disable_network_loopbacks)  
  
 [Iniciar a sessão de depuração](#BKMK_Start_the_debugging_session)  
  
-   [Iniciar a depuração (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Iniciar a depuração (F5), mas atrasar o início do aplicativo](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
 [Iniciar um aplicativo instalado no depurador](#BKMK_Start_an_installed_app_in_the_debugger)  
  
 [Anexar o depurador a um aplicativo em execução](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
-   [Definir o aplicativo para ser executado no modo de depuração](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
-   [Anexar o depurador](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a> A maneira fácil de iniciar a depuração  
 ![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
1.  Abra a solução do aplicativo no Visual Studio.  
  
2.  Se a solução contiver projetos para aplicativos da Windows Store e Windows Phone Store, verifique se o projeto que você quer depurar é o projeto de inicialização. No Gerenciador de Soluções, escolha o projeto e então selecione **Definir como Projeto de Inicialização** no menu de contexto.  
  
3.  Pressione F5.  
  
 ![Applies to Windows Phone only](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 O Visual Studio compila e inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim. Para obter mais informações, consulte [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a> Configurar a sessão de depuração  
 Como o script não está compilado, a configuração da compilação e as configurações da plataforma não se aplicam. Se você está depurando um componente C\+\+ ou gerenciado, defina a **Configuração** para **Depurar** e escolha sua plataforma de destino da caixa de diálogo **Configuração**.  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Abrir a página de propriedades de depuração do projeto  
  
1.  No Gerenciador de Soluções, selecione o projeto. No menu de atalho, escolha **Propriedades**.  
  
2.  Expanda o nó **Propriedades de Configuração** e selecione **Depuração**  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a> Escolher as opções de configuração de compilação  
  
1.  Na lista **Configuração**, escolha **Depurar** ou **\(Ativo\) Depurar**.  
  
2.  Na lista **Plataforma**, escolha a plataforma de destino da compilação. Na maioria dos casos, **Qualquer CPU** é a melhor opção.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a> Escolher o destino de implantação  
 Você pode implantar e depurar um aplicativo no computador com o Visual Studio, no simulador do Visual Studio do computador local ou de um computador remoto. Escolha o destino na lista **Depurador a iniciar** na página de propriedades **Depuração** do projeto.  
  
 ![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 No caso de um aplicativo da Windows Store, escolha uma dessas opções da lista **Dispositivo de destino**:  
  
|||  
|-|-|  
|**Computador Local**|Depure o aplicativo na sessão atual no computador local. Consulte [Executar aplicativos da Windows Store na máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [Executar aplicativos da Windows Store no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computador Remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente através de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [Executar aplicativos da Windows Store em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Se você escolher **Computador Remoto**, especifique o nome ou endereço IP do computador remoto de uma destas formas:  
  
-   Digite o nome ou o endereço IP do computador remoto na caixa **Nome do Computador**.  
  
-   Escolha a seta para baixo da caixa **Nome do Computador** e **\<Localizar...\>**. Em seguida, escolha o computador remoto na caixa de diálogo **Selecionar Conexão de Depurador Remoto**.  
  
     ![Selecione a conexão do depurador remoto](../debugger/media/vsrun_pro_selectremotedebuggerdlg.png "VSRUN\_PRO\_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  A caixa de diálogo Selecionar Conexão de Depurador Remoto exibe os computadores que estão na sub\-rede local e os computadores que estão diretamente conectados ao computador com o Visual Studio por um cabo Ethernet. Para especificar outro computador, digite o nome na caixa **Nome do Computador**.  
  
 ![Applies to Windows Phone only](../debugger/media/phone_only_content.png "phone\_only\_content")  
  
 No caso de um aplicativo da Windows Store, escolha **Dispositivo** ou um dos emuladores da lista **Dispositivo de destino**.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a> Escolher o depurador a ser usado  
 Por padrão, o depurador se anexa ao código JavaScript do aplicativo. Você pode escolher depurar o código C\+\+ nativo e gerenciado dos componentes do aplicativo em vez do código JavaScript. Especifique o código para depurar na lista **Tipo de Depurador** na página de propriedades **Depuração** do projeto de aplicativo.  
  
 Escolha um destes depuradores na lista **Tipo de depurador**:  
  
|||  
|-|-|  
|**Somente Script**|Depure o código JavaScript no aplicativo. O código gerenciado e o código nativo são ignorados.|  
|**Somente Nativo**|Depure o código C\/C\+\+ nativo no aplicativo. O código gerenciado e o código JavaScript são ignorados.|  
|**Nativo com script**|Depura o código C\+\+ nativo e o código JavaScript no aplicativo.|  
|**Somente Gerenciado**|Depura o código gerenciado no aplicativo. O código JavaScript e o código C\/C\+\+ nativo são ignorados.|  
|**Misto \(Gerenciado e Nativo\)**|Depura o código C\/C\+\+ nativo e o código gerenciado no aplicativo. O código JavaScript é ignorado.|  
  
###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> \(Opcional\) Atrasar o início do aplicativo na sessão de depuração  
 Por padrão, o Visual Studio inicia o aplicativo imediatamente quando você começa a depuração. Você também pode iniciar uma sessão de depuração, mas atrasar o início do seu aplicativo. O aplicativo é iniciado no depurador quando é iniciado do menu Iniciar ou por um contrato de ativação ou quando é iniciado por outro processo ou método. Você também pode usar o início atrasado para depurar eventos em segundo plano no aplicativo que você quer que ocorram quando o aplicativo não está em execução.  
  
 Especifique se deseja atrasar o início do aplicativo na lista **Iniciar Aplicativo** na página de propriedades **Depurando** do projeto do aplicativo. Escolha uma destas opções:  
  
-   Escolha **Não** para atrasar a inicialização do aplicativo.  
  
-   Escolha **Sim** para iniciar o aplicativo imediatamente.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a> \(Opcional\) Desabilitar loopbacks de rede  
 ![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Por motivos de segurança, um aplicativo da Windows Store instalado da maneira padrão não pode efetuar chamadas de rede para o dispositivo em que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo na Windows Store, você deve testá\-lo sem a isenção.  
  
 Para remover a isenção de loopback de rede, escolha **Não** na lista **Permitir Loopback de Rede** na página de propriedades **Depuração**.  
  
##  <a name="BKMK_Start_the_debugging_session"></a> Iniciar a sessão de depuração  
  
###  <a name="BKMK_Start_debugging__F5_"></a> Iniciar a depuração \(F5\)  
 Quando você escolhe **Iniciar Depuração** no menu **Depurar** \(teclado: F5\), o Visual Studio inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Iniciar a depuração \(F5\), mas atrasar o início do aplicativo  
 Você pode definir o aplicativo para ser executado no modo de depuração, mas deixar que ele inicie por outro método que não seja o depurador. Por exemplo, convém depurar a inicialização do aplicativo no menu Iniciar ou depurar um processo em segundo plano do aplicativo sem iniciá\-lo. Para atrasar o início do aplicativo, faça o seguinte:  
  
1.  Na página **Depurar** das propriedades do projeto do aplicativo, escolha **Não** da lista **Iniciar aplicativo**.  
  
2.  Escolha **Iniciar Depuração** no menu **Depurar** \(Teclado: F5\).  
  
3.  Inicie o aplicativo pelo menu Iniciar, por um contrato de execução ou por outro procedimento.  
  
 O aplicativo é iniciado no modo de depuração. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo seja encerrado.  
  
 Para obter mais informações sobre como depurar tarefas em segundo plano, consulte [Disparar eventos de suspensão, retomada e segundo plano para a Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Iniciar um aplicativo instalado no depurador  
 Quando você inicia a depuração usando F5, o Visual Studio compila e implanta o aplicativo, define que ele seja executado no modo de depuração e, em seguida, inicia\-o. Para iniciar um aplicativo que já está instalado em um dispositivo, use a caixa de diálogo Depurar Pacote do Aplicativo Instalado. Esse procedimento é útil quando você precisa depurar um aplicativo instalado da Windows Store ou quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para o aplicativo. Por exemplo, você pode ter um sistema de compilação personalizado que não use soluções ou projetos do Visual Studio.  
  
 O aplicativo pode ser instalado no dispositivo local ou em um dispositivo remoto. É possível iniciar o aplicativo imediatamente ou defini\-lo para ser executado no depurador quando for iniciado por outro processo ou método, por exemplo, no menu Iniciar ou por um contrato de ativação. Você também pode definir o aplicativo para ser executado no modo de depuração quando quiser depurar um processo em segundo plano sem iniciar o aplicativo. Para obter mais informações, consulte [Disparar eventos de suspensão, retomada e segundo plano para a Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Para definir um aplicativo instalado para ser executado no modo de depuração, faça isto:  
  
> [!NOTE]
>  O aplicativo não deve estar em execução quando você iniciar este procedimento.  
  
1.  No menu **Depurar**, escolha **Depurar Pacote do Aplicativo Instalado**  
  
2.  Escolha uma destas opções na lista:  
  
    |||  
    |-|-|  
    |**Computador Local**|Depure o aplicativo na sessão atual no computador local. Consulte [Executar aplicativos da Windows Store na máquina local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [Executar aplicativos da Windows Store no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Computador Remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente através de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [Executar aplicativos da Windows Store em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Escolha o aplicativo na lista **Pacotes de Aplicativo Instalados**.  
  
4.  Escolha o mecanismo de depuração a ser usado na lista **Depurar esse tipo de código**.  
  
5.  \(Opcional\). Escolha **Não iniciar, mas depurar meu código quando iniciar** para depurar o aplicativo quando ele for iniciado por outro método ou para depurar um processo em segundo plano.  
  
 Quando você clicar em **Iniciar**, o aplicativo será iniciado ou definido para ser executado no modo de depuração.  
  
##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Anexar o depurador a um aplicativo em execução  
 Para anexar o depurador a um aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], você deve usar o Gerenciador de Pacotes Depuráveis para definir a execução do aplicativo no modo de depuração. Esse recurso é instalado com as Ferramentas Remotas do Visual Studio.  
  
 Anexar o depurador a um aplicativo é útil quando você precisa depurar um aplicativo já instalado; por exemplo, um que tenha sido instalado na Windows Store. A anexação é necessária quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para ele. Por exemplo, você pode ter um sistema de compilação personalizado que não use projetos ou soluções do Visual Studio.  
  
 Para anexar a um aplicativo:  
  
1.  Defina o aplicativo para ser executado no modo de depuração. Isso deve ser feito quando o aplicativo não estiver em execução.  
  
2.  Inicie o aplicativo. Você pode iniciar o aplicativo no menu Iniciar, de um contrato de execução ou usando outro método.  
  
3.  Anexe o depurador ao aplicativo em execução.  
  
###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Definir o aplicativo para ser executado no modo de depuração  
  
1.  Instale as Ferramentas Remotas do Visual Studio no dispositivo em que o aplicativo está instalado. Consulte [Instalando as ferramentas remotas](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  No menu Iniciar, procure por `Debuggable Package Manager` e inicie\-o.  
  
     É exibida uma janela do PowerShell corretamente configurada para o cmdlet AppxDebug.  
  
3.  Para habilitar a depuração de um aplicativo, é preciso especificar o identificador PackageFullName do aplicativo. Para ver uma lista de todos os aplicativos que incluem o PackageFullName, digite `Get-AppxPackage` no aviso do PowerShell.  
  
4.  No aviso do PowerShell, digite `Enable-AppxDebug` *PackageFullName*, em que *PackageFullName* é o identificador PackageFullName do aplicativo.  
  
###  <a name="BKMK_Attach_the_debugger"></a> Anexar o depurador  
  
> [!TIP]
>  Os aplicativos JavaScript são executados em uma instância do processo wwahost.exe. Se outros aplicativos JavaScript estiverem em execução quando você anexa ao aplicativo, será necessário saber a ID do processo numérico \(PID\) do wwahost.exe em que o aplicativo está executando.  
>   
>  A maneira mais fácil de lidar com essa situação é fechar todos os outros aplicativos JavaScript. Do contrário, você pode abrir o Gerenciador de Tarefas do Windows antes de iniciar o aplicativo e observar as IDs dos processos wwahost.exe. Quando você especificar o processo ao qual anexar na caixa de diálogo **Processos disponíveis**, o wwahost.exe do aplicativo terá uma ID diferente daquelas que você observou.  
  
 Para anexar o depurador:  
  
1.  No menu **Depurar**, escolha **Anexar ao Processo**.  
  
     A caixa de diálogo **Anexar ao Processo** aparece.  
  
2.  Para anexar a um aplicativo em um dispositivo remoto, especifique o dispositivo remoto na caixa **Qualificador**. Você pode:  
  
    -   Digitar o nome na caixa **Qualificador**.  
  
    -   Escolha a seta para baixo na caixa **Qualificador** e escolha o dispositivo em uma lista de dispositivo já anexados antes.  
  
    -   Escolha **Localizar** para escolher o dispositivo em uma lista de dispositivos na sua sub\-rede local.  
  
3.  Especifique o tipo de código que você deseja depurar na caixa **Anexar a**.  
  
     Escolha **Selecionar** e faça o seguinte:  
  
    -   Escolha **Determinar automaticamente o tipo de código a ser depurado**  
  
    -   Escolha **Depurar estes tipos de código** e selecione um ou mais tipos na lista.  
  
4.  Na lista de **Processos Disponíveis**, escolha o processo **wwahost.exe** apropriado. Use a coluna **Título** para identificar seu aplicativo.  
  
5.  Escolha **Anexar**.  
  
 O Visual Studio anexa o depurador ao processo. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao seja encerrado.  
  
## Consulte também  
 [Controlar a execução em uma sessão de depuração \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Disparar eventos de suspensão, retomada e segundo plano para a Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)