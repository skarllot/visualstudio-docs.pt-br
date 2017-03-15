---
title: "Executar aplicativos da Windows Store em um computador remoto | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
caps.latest.revision: 43
caps.handback.revision: 43
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Executar aplicativos da Windows Store em um computador remoto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 O aplicativo ferramentas remotas do Visual Studio permite executar, depurar, analisar e testar um aplicativo da Windows Store em execução em um dispositivo de um segundo computador que está executando o Visual Studio.  Em execução em um dispositivo remoto pode ser especialmente eficaz quando o computador do Visual Studio não oferece suporte a funcionalidade específica para aplicativos da Windows Store, como toque, localização geográfica e orientação física.  Este tópico descreve os procedimentos para configurar e iniciar uma sessão remota.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 Você pode aprender:  
  
 [Pré-requisitos](#BKMK_Prerequisites)  
  
 [Segurança](#BKMK_Security)  
  
 [Como se conectar diretamente a um dispositivo remoto](#BKMK_DirectConnect)  
  
 [Instalando as Ferramentas Remotas](#BKMK_Installing_the_Remote_Tools)  
  
 [Iniciando o Monitor de depuração remota](#BKMK_Starting_the_Remote_Debugger_Monitor)  
  
 [Configurando o depurador remoto](#BKMK_ConfigureRemoteDebugger)  
  
 [Configurando o projeto do Visual Studio para depuração remota](#BKMK_ConnectVS)  
  
-   [Escolhendo o dispositivo remoto para projetos c# e Visual Basic](#BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects)  
  
-   [Escolhendo o dispositivo remoto para projetos em JavaScript e C++](#BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects)  
  
 [Executando uma sessão de depuração remota](#BKMK_RunRemoteDebug)  
  
##  <a name="BKMK_Prerequisites"></a> Pré\-requisitos  
 Para depurar em um dispositivo remoto:  
  
-   O dispositivo remoto e o computador com o Visual Studio devem estar conectados por uma rede ou diretamente por um cabo Ethernet.  Não há suporte à depuração pela Internet.  
  
-   Uma licença de desenvolvedor deve ser instalada no dispositivo remoto.  
  
-   O dispositivo remoto deve estar executando os componentes de depuração remota.  
  
-   Você deve ser um administrador no dispositivo remoto para configurar o firewall durante a instalação.  Você deve ter acesso de usuário ao dispositivo remoto para executar ou se conectar ao depurador remoto.  
  
##  <a name="BKMK_Security"></a> Segurança  
 Por padrão, o depurador remoto usa a autenticação do Windows.  
  
> [!WARNING]
>  Você também pode optar por executar o depurador remoto no modo sem autenticação, mas isso é altamente desaconselhável.  Nesse modo, não há nenhuma segurança de rede.  Escolha o Modo Sem Autenticação somente se você tiver certeza de que a rede não corre risco de receber tráfego mal\-intencionado ou hostil.  
  
##  <a name="BKMK_DirectConnect"></a> Como se conectar diretamente a um dispositivo remoto  
 Para se conectar diretamente a um dispositivo remoto, conecte o computador do Visual Studio para o dispositivo com um cabo Ethernet padrão.  Se o dispositivo não tem uma porta Ethernet, você pode usar um adaptador USB para Ethernet para se conectar ao cabo.  
  
##  <a name="BKMK_Installing_the_Remote_Tools"></a> Instalando as Ferramentas Remotas  
  
> [!NOTE]
>  **Versões e atualizações**  
>   
>  O**Ferramentas remotas para Visual Studio de 2015**não há suporte para versões anteriores do Visual Studio.  
>   
>  Recomendamos que você instale a versão de atualização das ferramentas remotas para Visual Studio de 2015 que corresponde à versão de atualização de sua instalação do Visual Studio.  
>   
>  O depurador do VS é compatível com qualquer combinação de versões do VS 2015 e as ferramentas remotas para VS 2015.  No entanto, o recurso mais recente do Visual Studio exige que o Visual Studio e as Ferramentas Remotas estejam na versão mais atualizada.  
>   
>  Outras ferramentas de diagnóstico podem exigir as mesmas versões das ferramentas remotas e do Visual Studio.  
  
 **Instalando os componentes de depuração remota em um dispositivo remoto**  
  
 Para executar ou salvar o programa de instalação das ferramentas remotas, escolha um dos links nesta tabela que corresponda ao sistema operacional do dispositivo remoto:  
  
### Visual Studio 2013  
  
|||||  
|-|-|-|-|  
|**Versão de atualização**|**X86**|**X64**|**ARM**|  
|**RTM**|[Baixar](http://go.microsoft.com/fwlink/?LinkId=320706)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=320707)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=320708)|  
|**Atualização 1**|[Baixar](http://go.microsoft.com/fwlink/?LinkID=386599)|[Baixar](http://go.microsoft.com/fwlink/?LinkID=386600)|[Baixar](http://go.microsoft.com/fwlink/?LinkID=386601)|  
|**Atualização 2**|[Baixar](http://go.microsoft.com/fwlink/?LinkId=393218)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=393217)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=393216)|  
|**Atualização 3**|[Baixar](http://go.microsoft.com/fwlink/?LinkId=403046)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=403047)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=403048)|  
|**Atualização 4**|[Baixar](http://go.microsoft.com/fwlink/?LinkId=512599)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=512600)|[Baixar](http://go.microsoft.com/fwlink/?LinkId=512601)|  
  
### Visual Studio 2015  
  
|||||  
|-|-|-|-|  
|**Versão**|**X86**|**X64**|**ARM**|  
|**Visualizar**|[Baixar](http://download.microsoft.com/download/4/8/A/48A0EA60-6097-4BA5-B7D3-EAE49499E1FB/rtools_setup_x86.exe)|[Baixar](http://download.microsoft.com/download/4/8/A/48A0EA60-6097-4BA5-B7D3-EAE49499E1FB/rtools_setup_x64.exe)|[Baixar](http://download.microsoft.com/download/4/8/A/48A0EA60-6097-4BA5-B7D3-EAE49499E1FB/rtools_setup_arm.exe)|  
  
 É possível optar por baixar o programa de instalação ou executá\-lo imediatamente.  Ao executar o programa de instalação, aceite o contrato de usuário e clique em **Instalar**.  
  
 Por padrão, os componentes de depuração remota são instalados na pasta **C:\\Program Files\\Microsoft Visual Studio 14.0\\Common7\\IDE\\Remote Debugger**.  
  
##  <a name="BKMK_Starting_the_Remote_Debugger_Monitor"></a> Iniciando o Monitor de depuração remota  
  
> [!NOTE]
>  Como o depurador remoto configura o firewall para permitir a comunicação com o host do Visual Studio, você deve ser um administrador no dispositivo remoto quando você inicia o depurador remoto pela primeira vez.  
  
 Depois de ter instalado as ferramentas remotas, escolha**depurador remoto**sobre o**Iniciar**tela.  O**configuração de depuração remota**aparece na primeira vez que você iniciar o depurador remoto.  
  
 Sobre o**configuração de depuração remota**caixa de diálogo:  
  
1.  Se a API de serviços de Web do Windows não estiver instalado, escolha**instalar**  
  
2.  No**Configurar o Firewall do Windows**grupo, escolha as que você deseja permitir conexões com redes.  Somente as redes que o dispositivo está conectado ao estão habilitadas.  Você deve escolher pelo menos uma rede.  
  
3.  Escolha**configurar depuração remota**para definir as opções de firewall e iniciar o depurador remoto.  Abra o**Visual Studio Monitor de depuração remota**caixa de diálogo para dar aos usuários permissões para as ferramentas remotas e definir outras opções avançadas.  
  
4.  O**Visual Studio Monitor de depuração remota**caixa de diálogo é exibida.  Você pode dar aos usuários permissões para as ferramentas remotas e definir outras opções avançadas nessa caixa de diálogo.  
  
##  <a name="BKMK_ConfigureRemoteDebugger"></a> Configurando o depurador remoto  
 Você pode usar duas ferramentas para modificar a configuração do depurador remoto.  
  
1.  Sobre o**ferramentas**menu o**Visual Studio Monitor de depuração remota**:  
  
    1.  Escolha**opções**para alterar o número da porta, o modo de autenticação ou o intervalo de tempo limite do depurador remoto.  
  
    2.  Escolha**permissões**para adicionar ou remover usuários que têm permissão para depuração remota.  
  
        > [!NOTE]
        >  Permissões devem ser concedidas a cada conta de usuário que depurar remotamente.  
  
 Você usa o**o Assistente de configuração do depurador remoto**para definir opções avançadas para o depurador remoto.  Para abrir o assistente, escolha**o Assistente de configuração do depurador remoto**na tela inicial.  
  
1.  Sobre o**Configurar o depurador remoto do Visual Studio**página, você pode optar por executar o depurador remoto como um serviço.  Na maioria dos casos, a execução como um serviço não é necessária.  
  
2.  Sobre o**Configurar o Firewall do Windows para depuração**página, você pode adicionar ou remover o tipo de rede que você deseja que o depurador remoto para se conectar ao.  Somente as redes que o dispositivo está conectado ao estão habilitadas.  Você deve escolher pelo menos uma rede.  
  
##  <a name="BKMK_ConnectVS"></a> Configurando o projeto do Visual Studio para depuração remota  
 Especifique o dispositivo remoto para se conectar nas propriedades do projeto.  O procedimento varia dependendo da linguagem de programação.  Você pode digitar o nome de rede do dispositivo remoto, ou você pode selecioná\-lo na caixa de diálogo Selecionar conexão de depurador remoto.  
  
 ![Marque a caixa de diálogo conexão de depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
 A caixa de diálogo lista somente os dispositivos que estão na sub\-rede local do computador do Visual Studio e que estão executando o depurador remoto.  
  
> [!TIP]
>  Se você tiver problemas para se conectar a um dispositivo remoto, tente digitar o endereço IP do dispositivo.  Para determinar o endereço IP de um dispositivo, abra uma janela de comando e digite**ipconfig**.  O endereço IP é listado como**IPv4 Address**.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Escolhendo o dispositivo remoto para projetos c\# e Visual Basic  
 ![Gerenciado de propriedades do projeto para depuração remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN\_Managed\_ProjProp\_Remote")  
  
1.  Selecione o nome do projeto no Solution Explorer e escolha**propriedades**no menu de atalho.  
  
2.  Selecione**Depurar**.  
  
3.  Escolha**máquina remota**do**dispositivo de destino**lista.  
  
4.  Digite o nome de rede do dispositivo remoto no**máquina remota**caixa ou escolha**localizar**para escolher o dispositivo do**Selecionar conexão de depurador remoto**caixa de diálogo.  
  
###  <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Escolhendo o dispositivo remoto para projetos em JavaScript e C\+\+  
 ![Propriedades do projeto C&#43;&#43; para depuração remota](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN\_CPP\_ProjProp\_Remote")  
  
1.  Selecione o nome do projeto no Solution Explorer e escolha**propriedades**no menu de atalho.  
  
2.  Expanda o**Propriedades de configuração**nó e selecione**depuração**.  
  
3.  Escolha**depurador remoto**do**depurador a iniciar**lista.  
  
4.  Digite o nome de rede do dispositivo remoto no**nome da máquina**caixa ou clique na seta na caixa para escolher o dispositivo no**Selecionar conexão de depurador remoto**caixa de diálogo.  
  
##  <a name="BKMK_RunRemoteDebug"></a> Executando uma sessão de depuração remota  
 Iniciar, parar e navegar por uma sessão de depuração remota da mesma forma que uma sessão local.  Antes de iniciar a depuração, verifique se que o Monitor de depuração remota está em execução no dispositivo remoto.  
  
 Escolha**Iniciar depuração**sobre o**Depurar**menu \(teclado: F5\).  O projeto é recompilado, em seguida, implantado e iniciado no dispositivo remoto.  O depurador suspende a execução em pontos de interrupção, e você pode entrar em sobre e fora do seu código.  Escolha**parar depuração**para encerrar a sessão de depuração e fechar o aplicativo remoto.  Para obter mais informações, consulte[Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md).  
  
## Consulte também  
 [Testando aplicativos da Store com o Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)