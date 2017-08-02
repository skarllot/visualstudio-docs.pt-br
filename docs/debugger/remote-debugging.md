---
title: "Depura&#231;&#227;o remota | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.remote.overview"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "JScript"
  - "VB"
helpviewer_keywords: 
  - "configuração de depuração, remota"
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 76
caps.handback.revision: 48
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depura&#231;&#227;o remota
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode depurar um aplicativo do Visual Studio que foi implantado em um computador diferente.  Para fazer isso, você deve usar o depurador remoto do Visual Studio.  
  
 As informações aqui se aplica a aplicativos de área de trabalho do Windows e aplicativos ASP.NET.  Para obter informações sobre depuração remota da Windows Store de aplicativos e aplicativos do Azure, consulte [Depuração remota em aplicativos da Windows Store e o Azure](#bkmk_winstoreAzure).  
  
## Baixe e instale as ferramentas remotas  
 Você pode baixar as ferramentas remotas para depuração [Ferramentas remotas para Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48155). Você pode escolher x86, x64 e ARM versões das ferramentas. Quando terminar de baixar o arquivo executável, siga as instruções para instalar o aplicativo no computador remoto.  
  
 Você pode baixar a versão de atualização 2 das ferramentas remotas em [Ferramentas remotas para atualização 2 do Visual Studio 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs#d-remote-tools). Observe que a versão do ARM deste download oferece, na verdade, a versão de atualização 1 ARM das ferramentas remotas. Você pode usar as ferramentas remotas de atualização 1 ARM junto com a atualização 2 do Visual Studio 2015.  
  
 Você pode baixar a versão de atualização 1 das ferramentas remotas em [Ferramentas remotas para atualização 1 do Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=49986&44F86079-8679-400C-BFF2-9CA5F2BCBDFC=1).  
  
> [!IMPORTANT]
>  Você deve instalar a versão das ferramentas remotas que corresponde à versão da instalação do Visual Studio. Versões não correspondentes não são recomendadas.  
>   
>  Além disso, você deve instalar as ferramentas remotas que têm a mesma arquitetura do sistema operacional no qual você deseja instalá\-lo. Em outras palavras, se você deseja depurar um aplicativo de 32 bits em um um computador remoto executando um sistema operacional de 64 bits, você deve instalar a versão de 64 bits das ferramentas remotas no computador remoto.  
  
 Se o computador remoto já tiver o Visual Studio 2015 Community, Professional ou Enterprise já instalado, o depurador remoto \(**msvsmon.exe**\) já está instalado, e você poderá iniciá\-lo de seu diretório:  
  
 **\< diretório de instalação do visual Studio \> \\Common7\\IDE\\Remote Debugger\\\(x64, x86, Appx\)\\msvsmon.exe**  
  
 No entanto, o **o Assistente de configuração do depurador remoto** \(**rdbgwiz.exe**\) é instalado apenas quando você baixar e instalar as ferramentas, e talvez seja necessário usá\-la para a configuração mais tarde, especialmente se você deseja que o depurador remoto para ser executado como um serviço. Para obter mais informações, consulte [Configurar o depurador remoto como um serviço](#bkmk_configureService) abaixo.  
  
## Sistemas operacionais com suporte  
 O computador remoto deve estar executando um dos seguintes sistemas operacionais:  
  
-   Windows 10  
  
-   Windows 8 ou 8.1  
  
-   Windows 7 Service Pack 1  
  
-   Windows Server 2012 ou Windows Server 2012 R2  
  
-   Windows Server 2008 Service Pack 2, Windows Server 2008 R2 Service Pack 1  
  
## Configurações de Hardware com suporte  
  
-   1,6 GHz ou processador mais rápido  
  
-   1 GB de RAM \(1,5 GB se executado em uma máquina virtual\)  
  
-   1 GB de espaço em disco disponível  
  
-   Disco rígido de 5400 RPM  
  
-   Placa vídeo compatível com 9 DirectX em execução na resolução de 1024 x 768 ou superior  
  
## Configuração de rede  
 O computador remoto e o computador do Visual Studio devem ser conectados por uma rede, um grupo de trabalho ou um grupo doméstico, senão conectados diretamente por meio de um cabo Ethernet. Não há suporte para depuração pela Internet.  
  
## Configurar o depurador remoto  
 Você deve ter permissões administrativas no computador remoto  
  
1.  Localize o aplicativo do depurador remoto. Você pode procurar **depurador remoto** no **Iniciar** menu.  
  
2.  Quando você iniciar as ferramentas remotas pela primeira vez \(ou antes de você tê\-lo configurado\), o **configuração de depuração remota** dalog caixa é exibida.  
  
     ![RemoteDebuggerConfWizardPage](../debugger/media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3.  Se a API de serviço do Windows não estiver instalada \(o que acontece apenas no Windows Server 2008 R2\), escolha o **instalar** botão.  
  
4.  Selecione os tipos de rede que você deseja usar as ferramentas remotas. Pelo menos um tipo de rede deve ser selecionado. Se os computadores estiverem conectados por meio de um domínio, você deve escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo de trabalho ou um grupo doméstico, você precisa escolher o segundo ou terceiro item conforme apropriado.  
  
5.  Escolha **Configurar a depuração remota** para configurar o firewall e iniciar a ferramenta.  
  
6.  Quando a configuração estiver concluída, a janela do depurador remoto aparece.  
  
     ![RemoteDebuggerWindow](../debugger/media/remotedebuggerwindow.png "RemoteDebuggerWindow")  
  
 Você pode parar o depurador remoto clicando **arquivo \/ sair** na janela. Você poderá reiniciá\-lo do **Iniciar** menu ou da linha de comando:  
  
 **\\Common7\\IDE\\Remote Debugger\\ \< diretório de instalação do visual Studio \> \< x86, x64 ou Appx\\msvsmon.exe**.  
  
## Configurar o depurador remoto  
 Você pode alterar alguns aspectos da configuração do depurador remoto depois que você tiver iniciado pela primeira vez.  
  
-   Para permitir que outros usuários se conectem ao depurador remoto, escolha **Ferramentas \/ permissões**. Você deve ter privilégios de administrador para conceder ou negar permissões.  
  
-   Para alterar o modo de autenticação ou o número da porta ou especificar um valor de tempo limite para as ferramentas remotas: escolha Ferramentas \/ opções.  
  
     Para obter uma lista dos números de porta usados por padrão, consulte [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md).  
  
> [!WARNING]
>  Você pode optar por executar as ferramentas remotas no modo sem autenticação, mas esse modo é altamente desaconselhável. Nesse modo não há nenhuma segurança de rede. Escolha o modo sem autenticação somente se tiver certeza de que a rede não está em risco de tráfego mal\-intencionado ou hostil.  
  
##  <a name="bkmk_configureService"></a> Configurar o depurador remoto como um serviço  
 Para depuração no ASP.NET e outros ambientes de servidor, você precisa executar o depurador remoto como um serviço.  
  
1.  Encontre o **Assistente de configuração do depurador remoto** \(rdbgwiz.exe\). \(Isso é um aplicativo separado do depurador remoto.\) Ele está disponível apenas quando você instala as ferramentas remotas. Ele não é instalado com o Visual Studio.  
  
2.  Começar a executar o Assistente de configuração. Quando a primeira página é exibida, clique em **próximo**.  
  
3.  Verifique o **executar o depurador remoto do Visual Studio 2015 como um serviço** caixa de seleção.  
  
4.  Adicione o nome da conta de usuário e senha.  
  
     Talvez seja necessário adicionar o **fazer logon como um serviço** usuário direita para essa conta. \(Localizar **política de segurança Local** \(secpol. msc\) no **Iniciar** janela ou página \(ou tipo **secpol** em um prompt de comando\). Quando a janela for exibida, clique duas vezes em **atribuição de direitos de usuário**, localize **fazer logon como um serviço** no painel à direita. Clique duas vezes nele. Adicione a conta de usuário para o **propriedades** janela e clique em **OK**.\) Clique em **Avançar**.  
  
5.  Selecione o tipo de rede que você deseja se comunicar com as ferramentas remotas. Pelo menos um tipo de rede deve ser selecionado. Se os computadores estiverem conectados por meio de um domínio, você deve escolher o primeiro item. Se os computadores estiverem conectados por meio de um grupo de trabalho ou um grupo doméstico, você deve escolher os segundo ou terceiro itens. Clique em **Avançar**.  
  
6.  Se o serviço pode ser iniciado, você verá **você concluiu com êxito o Assistente de configuração de depurador Visual remoto Studio**. Se o serviço não pode ser iniciado, você verá **Falha ao concluir o Assistente de configuração de depurador Visual remoto Studio**. A página também fornece algumas dicas a seguir para iniciar o serviço.  
  
7.  Clique em **Concluir**.  
  
 Neste ponto, o depurador remoto está em execução como um serviço. Você pode verificar isso indo para **Painel de controle \/ serviços** e procurando **depurador remoto do Visual Studio 2015**.  
  
 Você pode parar e iniciar o serviço do depurador remoto do **Painel de controle \/ serviços**.  
  
## Executar o depurador remoto com diferentes contas de usuário  
 É possível executar o depurador remoto em uma conta de usuário diferente da conta de usuário que você está usando no computador do Visual Studio, mas você deve adicionar a conta de usuário diferente para as permissões do depurador remoto.  
  
-   Você pode iniciar o depurador remoto na linha de comando com o **\/Allow \< username \>** parâmetro: **msvsmon \/Allow \< username@computer \>**.  
  
-   Você pode adicionar o usuário com permissões do depurador remoto \(na janela do depurador remoto \(**Ferramentas \/ permissões**\).  
  
## Depuração remota um projeto do Visual C\+\+  
 No procedimento a seguir, o nome e caminho do projeto é C:\\remotetemp\\MyMfc e o nome do computador remoto é **remote1**.  
  
1.  Criar um aplicativo MFC chamado **mymfc.**  
  
2.  Definir um ponto de interrupção em algum lugar no aplicativo que é atingido facilmente, por exemplo, em **MainFrm.cpp**, no início de `CMainFrame::OnCreate`.  
  
3.  No Visual Studio, no **projeto** menu, selecione **propriedades**. Abra o **depuração** guia.  
  
4.  Definir o **depurador a iniciar** para **depurador remoto do Windows**.  
  
     ![RemoteDebuggingCPlus](../debugger/media/remotedebuggingcplus.png "RemoteDebuggingCPlus")  
  
5.  Faça as seguintes alterações para as propriedades:  
  
    |||  
    |-|-|  
    |**Configuração**|**Valor**|  
    |Comando remoto|C:\\remotetemp\\mymfc.exe.|  
    |Diretório de trabalho|C:\\remotetemp.|  
    |Nome do servidor remoto|remote1|  
    |Conexão|Remoto com autenticação do Windows|  
    |Tipo de Depurador|Somente Nativo|  
    |Diretório de implantação|C:\\remotetemp..|  
    |Arquivos adicionais para implantar|C:\\data\\mymfcdata.txt..|  
  
6.  Na barra de ferramentas, abra o **configuração da solução** menu suspenso e escolha **do Configuration Manager**.  
  
7.  Para o **Depurar** configuração, selecione o **implantar** caixa de seleção.  
  
     ![RemoteDebugCplusDeploy](~/debugger/media/remotedebugcplusdeploy.png "RemoteDebugCplusDeploy")  
  
8.  Iniciar a depuração \(**Depurar \/ iniciar depuração**, ou **F5**\).  
  
9. O executável é implantado automaticamente ao computador remoto.  
  
10. No computador do Visual Studio, você verá que a execução é interrompida no ponto de interrupção.  
  
    > [!TIP]
    >  Como alternativa, você pode implantar os arquivos como uma etapa separada. No **Gerenciador de soluções,** com o botão direito do **mymfc** nó e escolha **implantar**.  
  
 Se você tiver arquivos de código não precisam ser usados pelo aplicativo, você precisa incluí\-los no projeto do Visual Studio. Crie uma pasta de projeto para os arquivos adicionais \(no **Solution Explorer**, clique em **Adicionar \/ nova pasta**.\) Em seguida, adicione os arquivos na pasta \(em S**Soluçã Explorer**, clique em **Adicionar \/ existente Item**, em seguida, selecione os arquivos.\). Sobre o **propriedades** página para cada arquivo, defina **Copy to Output Directory** para **Copiar sempre**.  
  
## Depuração remota um projeto Visual c\# ou Visual Basic  
 O depurador não pode implantar aplicativos de desktop Visual c\# ou Visual Basic para um computador remoto, mas você ainda pode depurá\-los remotamente da seguinte maneira. O procedimento a seguir pressupõe que você deseja depurá\-lo em um computador chamado **remote1**.  
  
1.  Crie um projeto chamado **MyWpf**.  
  
2.  Defina um ponto de interrupção em algum lugar no código que é facilmente acessado. Por exemplo, você pode definir um ponto de interrupção em um manipulador do botão.  
  
3.  Sobre o **projeto** menu, escolha **propriedades**.  
  
4.  Sobre o **propriedades** página, escolha o **Depurar** guia.  
  
     ![RemoteDebuggerCSharp](../debugger/media/remotedebuggercsharp.png "RemoteDebuggerCSharp")  
  
5.  Verifique se o **diretório de trabalho** caixa de texto está vazia.  
  
6.  Escolha **usar computador remoto**, e o tipo **remote1** na caixa de texto.  
  
7.  Verifique se **Habilitar a depuração de código nativo** não estiver selecionada.  
  
8.  Compile o projeto.  
  
9. Crie uma pasta no computador remoto que é o mesmo caminho de **Depurar** pasta no seu computador do Visual Studio: **\< caminho de origem \> \\MyWPF\\MyWPF\\bin\\Debug**.  
  
10. Copie o executável que você acabou de criar do seu computador do Visual Studio para a pasta recém\-criada no computador remoto.  
  
    > [!CAUTION]
    >  Não faça alterações no código ou recompilar antes desta etapa. O executável que você copiou para o computador remoto deve corresponder exatamente o local de origem e símbolos.  
  
11. No Visual Studio, inicie a depuração \(**Depurar \/ iniciar depuração**, ou **F5**\).  
  
12. Verifique se o ponto de interrupção. Você verá que o ponto de interrupção está ativo. Caso contrário, os símbolos para o aplicativo ainda não carregado. Para obter informações sobre carregamento de símbolos e como solucionar esses problemas, consulte [configurações de símbolo Noções básicas sobre arquivos de símbolo e o Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/05/understanding-symbol-files-and-visual-studio-s-symbol-settings.aspx).  
  
13. Você verá que a janela principal do aplicativo do WPF é aberta no computador remoto. Execute a ação que faz com que o ponto de interrupção seja atingido.  
  
14. Na máquina do Visual Studio, você verá que a execução foi interrompida no ponto de interrupção.  
  
 Se você tiver arquivos de código não precisam ser usados pelo aplicativo, você precisa incluí\-los no projeto do Visual Studio. Crie uma pasta de projeto para os arquivos adicionais \(no **Solution Explorer**, clique em **Adicionar \/ nova pasta**.\) Em seguida, adicione os arquivos na pasta \(em S**Soluçã Explorer**, clique em **Adicionar \/ existente Item**, em seguida, selecione os arquivos.\). Sobre o **propriedades** página para cada arquivo, defina **Copy to Output Directory** para **Copiar sempre**.  
  
## Depurar remotamente um aplicativo ASP.NET  
 Implantar um aplicativo ASP.NET em um computador remoto executando o IIS tem etapas diferentes, dependendo do sistema operacional e a versão do IIS. Para computadores remotos que executam o Windows 8 ou posterior ou Windows Server 2012 sistemas operacionais com o IIS 8 \(ou posterior\) instalada, consulte [Publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Para computadores remotos executando o Windows 7 ou Windows Server 2008 com o IIS 7.5 instalado, consulte [Depuração ASP.NET em um servidor remoto 7.5 remota do computador](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
## Configurar a depuração com símbolos remotos  
 Você deve ser capaz de depurar seu código com os símbolos gerado no computador do Visual Studio. O desempenho do depurador remoto é muito melhor quando você usa símbolos locais. Se você precisar usar símbolos remotos, você precisa informar o monitor de depuração remota para procurar por símbolos no computador remoto.  
  
 A partir do Visual Studio 2013 atualização 2, você pode usar a seguinte opção de linha de comando do msvsmon usar símbolos remotos para código gerenciado: `Msvsmon / /FallbackLoadRemoteManagedPdbs`  
  
 Para obter mais informações, consulte a Ajuda de depuração remota \(pressione **F1** na janela do depurador remoto, ou clique em **Ajuda \/ uso**\). Você pode encontrar mais informações em [remoto símbolo carregar alterações do .NET no Visual Studio 2012 e 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)  
  
##  <a name="bkmk_winstoreAzure"></a> Depuração remota em aplicativos da Windows Store e o Azure  
 Para obter informações sobre a depuração remota com aplicativos da Windows Store, consulte [Depurar e testar aplicativos da Windows Store em um dispositivo remoto do Visual Studio](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx).  
  
 Para obter informações sobre depuração no Azure, consulte um destes tópicos:  
  
-   [Depuração de um serviço de nuvem ou máquina Virtual no Visual Studio](http://msdn.microsoft.com/library/azure/ff683670.aspx)  
  
-   [Depurando back\-end do .NET no Visual Studio](http://blogs.msdn.com/b/azuremobile/archive/2014/03/14/debugging-net-backend-in-visual-studio.aspx)  
  
-   Introdução à depuração remota em Sites do Azure \([parte 1](http://azure.microsoft.com/blog/2014/05/06/introduction-to-remote-debugging-on-azure-web-sites/), [parte 2](http://azure.microsoft.com/blog/2014/05/07/introduction-to-remote-debugging-azure-web-sites-part-2-inside-remote-debugging/), [parte 3](http://azure.microsoft.com/blog/2014/05/08/introduction-to-remote-debugging-on-azure-web-sites-part-3-multi-instance-environment-and-git/)\).  
  
## Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Configurar o Firewall do Windows para a depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md)   
 [Depuração ASP.NET em um servidor remoto 7.5 remota do computador](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)