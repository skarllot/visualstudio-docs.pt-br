---
title: "Defini&#231;&#245;es do projeto para uma configura&#231;&#227;o de depura&#231;&#227;o do C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDebugSettings.WebBrowser.DebuggerType"
  - "VC.Project.IVCGPUDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.SymbolPath"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationCommand"
  - "VC.Project.IVCRemoteDebugPageObject.WorkingDirectory"
  - "VC.Project.VCDebugSettings.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.SQLDebugging"
  - "VC.Project.IVCRemoteDebugPageObject.Remote"
  - "VC.Project.IVCGPUDebugPageObject.CommandArguments"
  - "VC.Project.VCDebugSettings.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.SQLDebugging"
  - "VC.Project.IVCWebSvcDebugPageObject.HttpUrl"
  - "VC.Project.IVCLocalDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunCommand"
  - "VC.Project.IVCGPUDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCWebSvcDebugPageObject.DebuggerType"
  - "VC.Project.IVCRemoteDebugPageObject.CommandArguments"
  - "VC.Project.IVCRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteMachine"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter"
  - "VC.Project.IVCGPUDebugPageObject.RemoteConnection"
  - "VC.Project.VCDebugSettings.PDBPath"
  - "VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory"
  - "VC.Project.VCDebugSettings.SQLDebugging"
  - "VC.Project.VCDebugSettings.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ShimCommand"
  - "VC.Project.IVCLocalDebugPageObject.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCLocalDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationArguments"
  - "VC.Project.IVCLocalDebugPageObject.Environment"
  - "VC.Project.IVCGPUDebugPageObject.DeploymentDirectory"
  - "VC.Project.IVCLocalDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.Environment"
  - "VC.Project.IVCGPUDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCLocalDebugPageObject.DebuggerType"
  - "VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl"
  - "VC.Project.IVCWebSvcDebugPageObject.SQLDebugging"
  - "VC.Project.IVCGPUDebugPageObject.AcceleratorType"
  - "VC.Project.IVCGPUDebugPageObject.Environment"
  - "VC.Project.VCDebugSettings.RemoteMachine"
  - "VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy"
  - "VC.Project.VCDebugSettings.WorkingDirectory"
  - "vs.debug.builds"
  - "VC.Project.VCDebugSettings.Attach"
  - "VC.Project.VCDebugSettings.HttpUrl"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptMode"
  - "VC.Project.IVCGPUDebugPageObject.Attach"
  - "VC.Project.IVCRemoteDebugPageObject.AdditionalFiles"
  - "VC.Project.IVCGPUDebugPageObject.Command"
  - "VC.Project.VCDebugSettings.Remote"
  - "VC.Project.IVCRemoteDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.EnvironmentMerge"
  - "VC.Project.IVCGPUDebugPageObject.MachineName"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "arquivos .pdb, depurar configurações de projeto de compilação"
  - "Opção de vinculador /DEBUG"
  - "Opção de vinculador /MAP"
  - "Opção de vinculador /MAPINFO"
  - "Opção de vinculador /PDB"
  - "Opção de vinculador /PDBSTRIPPED"
  - "Opção de compilador /Z7 (C++)"
  - "Opção de compilador /Zd (C++)"
  - "/ZI [C++] - opção do compilador"
  - "depurar compilações, configurações de projeto"
  - "depurar configurações, C++"
  - "opção de vinculador DEBUG"
  - "opção de vinculador -DEBUG"
  - "depurando [C++], depurando configurações"
  - "opção de vinculador MAP"
  - "opção de vinculador -MAP"
  - "arquivos de mapa, configurações de projeto"
  - "opção de vinculador MAPINFO"
  - "opção de vinculador -MAPINFO"
  - "arquivos pdb, depurar configurações de projeto de compilação"
  - "opção de vinculador PDB"
  - "opção de vinculador -PDB"
  - "opção de vinculador PDBSTRIPPED"
  - "opção de vinculador -PDBSTRIPPED"
  - "configurações do projeto, depurar"
  - "configurações do projeto [Visual Studio]"
  - "configurações do projeto [Visual Studio], depurar configurações"
  - "projetos [Visual Studio], depurar configurações"
  - "Opção de compilador Z7 [C++]"
  - "Opção de compilador -Z7 [C++]"
  - "Opção de compilador Zd [C++]"
  - "Opção de compilador -Zd [C++]"
  - "ZI [C++] - opção do compilador"
  - "Opção de compilador -Zl [C++]"
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Defini&#231;&#245;es do projeto para uma configura&#231;&#227;o de depura&#231;&#227;o do C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode alterar as configurações do projeto para uma configuração de depuração C ou Visual C\+\+ na caixa de diálogo **Páginas de Propriedades**, conforme discutido em [Como definir configurações de depuração e versão](../debugger/how-to-set-debug-and-release-configurations.md).  As tabelas a seguir mostram onde localizar configurações relacionadas ao depurador na caixa de diálogo **Páginas de Propriedades**.  
  
> [!WARNING]
>  As configurações de projeto de depuração na categoria de **Propriedades de Configuração\/Depuração** para aplicativos do Windows Store e componentes que são escritos em C\+\+ são diferentes.  Consulte [Iniciar uma sessão de depuração \(VB, C\#, C\+\+ e XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) no Centro de Desenvolvimento do Windows.  
  
 Especifique qual depurador usar na caixa de listagem **Depurador a iniciar**.  Sua escolha afetará as propriedades visíveis.  
  
 Cada configuração de propriedade de depuração é automaticamente gravada e salva no arquivo “por usuário” \(.vcxproj.user\) para sua solução sempre que você salve sua solução.  
  
### A pasta propriedades de configuração \(categoria de depuração\)  
  
|**Configuração**|**Descrição**|  
|----------------------|-------------------|  
|**Depurador a iniciar**|Especifica o depurador para executar, com as seguintes opções:<br /><br /> -   **Depurador Local do Windows**<br />-   **Depurador Remoto do Windows**<br />-   **Depurador do navegador da Web**<br />-   **Depurador de serviço Web**|  
|**Comando** \(Depurador Local do Windows\)|Especifica o comando para iniciar o programa que você está depurando no computador local.|  
|**Comando Remoto** \(Depurador Remoto do Windows\)|O caminho para o .exe no computador remoto.  Digite o caminho exatamente como você o digitaria no computador remoto.|  
|**Argumentos do Comando** \(Depurador Local do Windows e Depurador Remoto do Windows\)|-   Especifica argumentos para o comando especificado anteriormente.<br /><br /> Você pode usar os seguintes operadores de redirecionamento nesta caixa:<br /><br /> \< `file`<br /> Lê o stdin do arquivo.<br /><br /> \> `file`<br /> Grava stdout no arquivo.<br /><br /> \>\> `file`<br /> Acrescenta o stdout ao arquivo.<br /><br /> 2\> `file`<br /> Grava stderr no arquivo.<br /><br /> 2\>\> `file`<br /> Acrescenta o stderr ao arquivo.<br /><br /> 2\> &1<br /> Envia a saída de stderr \(2\) para a mesma localidade que o stdout \(1\).<br /><br /> 1\> &2<br /> Envia a saída de stdout \(1\) para a mesma localidade que o stderr \(2\).<br /><br /> Na maioria dos casos, esses operadores serão aplicáveis somente para aplicativos de console.|  
|**Diretório de trabalho**|Especifica o diretório de trabalho do programa que está sendo depurado, relativo ao diretório do projeto onde o EXE está localizado.  Se você deixar isso em branco, o diretório de trabalho será o diretório do projeto.  A depuração remota, o diretório do projeto será no servidor remoto.|  
|**Anexar** \(Depurador Local do Windows e Depurador Remoto do Windows\)|Especifica se inicia ou anexa ao aplicativo.  A configuração padrão é Não.|  
|**Nome do Servidor Remoto** \(Depurador Remoto do Windows\)|Especifica o nome de um computador \(diferente do seu\) no qual você deseja depurar um aplicativo.<br /><br /> A macro de compilação RemoteMachine é definida com o valor desta propriedade; para obter mais informações, consulte [Macros para comandos e propriedades de compilação](/visual-cpp/ide/common-macros-for-build-commands-and-properties).|  
|**Conexão** \(Depurador Remoto do Windows\)|Permite que você alterne entre tipos de conexão padrão e sem autenticação para depuração remota.  Especifique um nome do computador remoto na caixa de **Nome do Servidor Remoto**.  Tipos de conexão incluem o seguinte:<br /><br /> -   **Remoto sem Autenticação do Windows**<br />-   **Remoto sem Autenticação \(nativo somente\)**<br /><br /> **Observação** Depuração remota sem a autenticação pode deixar o computador remoto vulnerável às violações de segurança.  O modo de Autenticação do Windows é mais seguro.<br /><br /> Para obter mais informações, consulte [Configuração de depuração remota](../debugger/remote-debugging.md).|  
|**URL HTTP** \(depurador de serviço Web e depurador de navegador da Web\)|Especifica a URL no qual o projeto que você está depurar está localizado.|  
|**Tipo de Depurador**|Especifica o tipo de depurador a ser usado: **Apenas Nativo**, **Gerenciado Somente**, **Somente GPU**, **Misto**, **Automático** \(padrão\) ou **Script**.<br /><br /> -   **Apenas Nativo** é para código C\+\+ não gerenciado.<br />-   **Gerenciado Somente** é para código executado sob o common language runtime \(código gerenciado\).<br />-   **Misto** invoca depuradores para código gerenciado e não gerenciado.<br />-   **Automático** determina o tipo do depurador com base no compilador e as informações de EXE.<br />-   **Script** chama um depurador para scripts.<br />-   **Somente GPU** é para o código C\+\+ AMP que é executado em um dispositivo GPU ou no rasterizador de referência de DirectX.  Consulte [Depurando código de GPU](../debugger/debugging-gpu-code.md).|  
|**Ambiente** \(Depurador Local do Windows\)|Especifica variáveis de ambiente para o programa que você está depurando.  Use a sintaxe padrão da variável de ambiente \(por exemplo, `PATH="%SystemRoot%\…"`\).  Essas variáveis substituem o ambiente do sistema ou são mescladas com o ambiente do sistema, dependendo da configuração de **Ambiente de Mesclagem**.  Quando você clica na coluna de configurações, uma opção "Editar..." aparece.  Clique nesse link para editar variáveis de ambiente.|  
|**Ambiente de Mesclagem** \(Depurador Local do Windows\)|Determina se as variáveis que são especificadas na caixa **Ambiente** serão mescladas com o ambiente definido pelo sistema operacional.  A configuração padrão é Sim.|  
|**Depuração de SQL** \(todos, com exceção do Depurador do Conjunto de MPI\)|Permite a depuração de procedimentos SQL do seu aplicativo [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)].  A configuração padrão é Não.|  
|**Tipo de Acelerador de Depuração** \(somente depuração de GPU\)|Especifica o dispositivo GPU a ser usado para depuração.  A instalação de drivers de dispositivo para dispositivos compatíveis com GPU adicionará outras opções.  A configuração padrão é “GPU \- emulador de software.”|  
|**Comportamento de ponto de interrupção padrão GPU** \(somente depuração de GPU\)|Especifica se um evento de ponto de interrupção deve ser gerado para cada thread em um warp SIMD.  A configuração padrão é gerar o evento do ponto de interrupção apenas uma vez por encurvamento.|  
|**Acelerador Padrão do AMP** \(somente depuração de GPU\)|Especifica o acelerador padrão de AMP ao depurar o código de GPU.  Escolha **Acelerador de software WARP** para investigar se um problema é causado por hardware ou por um driver em vez de por seu código.|  
|**Diretório de Implantação** \(Depurador Remoto do Windows\)|Especifica o caminho no computador remoto onde a saída do projeto será copiada antes da inicialização.  O caminho pode ser um compartilhamento de rede no computador remoto, ou pode ser um caminho para uma pasta no computador remoto.  A configuração padrão está vazia, o que significa que a saída do projeto não é copiada para um compartilhamento de rede.  Para ativar a implantação de arquivos, você também deve marcar a caixa de seleção **Implementar** na caixa de diálogo Gerenciador de Configurações.  Para obter mais informações, consulte [Como criar e editar configurações de teste](../ide/how-to-create-and-edit-configurations.md).|  
|**Arquivos adicionais para implantar** \(depurador remoto do Windows\)|Se a propriedade do diretório de implantação estiver definida, esta é uma lista delimitada por ponto\-e\-vírgula de arquivos adicionais a serem copiados para o diretório de implantação.  A configuração padrão está vazia, o que significa que nenhum arquivo adicional é copiado para o diretório de implantação.  Para ativar a implantação de arquivos, você também deve marcar a caixa de seleção **Implementar** na caixa de diálogo Gerenciador de Configurações.  Para obter mais informações, consulte [Como criar e editar configurações de teste](../ide/how-to-create-and-edit-configurations.md).|  
|**Implantar Bibliotecas de Runtime do Visual C\+\+ Debug** \(Depurador Remoto do Windows\)|Se a propriedade do diretório de implantação estiver definida, isso especifica se as bibliotecas em tempo de execução de depuração do Visual C\+\+ da plataforma atual devem ser copiadas para o compartilhamento de rede.  A configuração padrão é Sim.|  
  
### Pasta C\/C\+\+ \(Categoria geral\)  
  
|Configuração|Descrição|  
|------------------|---------------|  
|**Formato de Informação de Depuração** \([\/Z7, \/Zd, Zi, \/ZI](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\)|Especifica o tipo de informação de depuração a ser criada para o projeto.<br /><br /> A opção padrão \(\/ZI\) cria um banco de dados \(PDB\) do programa no formato Editar e Continuar compatível.  Para obter mais informações, consulte [\/Z7, \/Zd, \/Zi, \/ZI \(formato de informação de depuração\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format).|  
  
### Pasta C\/C\+\+ \(Categoria de otimização\)  
  
|Configuração|Descrição|  
|------------------|---------------|  
|**Otimização**|Especifica se o compilador deve otimizar o código que produz.  A otimização altera o código que é executado.  O código otimizado não corresponde ao código\-fonte.  Portanto, a depuração é difícil.<br /><br /> A opção padrão \(**Desabilitado \(\/0d**\) suprime a otimização.  Você pode desenvolver com a otimização suprimida e, em seguida, habilitá\-la quando você criar a versão de produção do seu código.|  
  
### Pasta do vinculador \(categoria de depuração\)  
  
|Configuração|Descrição|  
|------------------|---------------|  
|**Gerar informações de depuração** \([\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info)\)|Informe ao vinculador para incluir informações de depuração, que terá o formato especificado por \/Z7, por \/Zd, por Zi, ou por \/ZI.|  
|**Gerar arquivo de banco de dados de programa** \([\/PDB:name](/visual-cpp/build/reference/pdb-use-program-database)\)|Especifique o nome de um arquivo de PDB nesta caixa.  Você deve selecionar ZI ou \/Zi para obter o formato de informações de depuração.|  
|**Segmentar Símbolos Privados** \([\/PDBSTRIPPED:filename](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)\)|Especifique o nome de um arquivo de PDB nesta caixa, caso não queira incluir símbolos particulares no arquivo de PDB.  Esta opção cria um segundo arquivo \(PDB\) de banco de dados do programa quando você compila a imagem do programa com qualquer uma das opções de compilador ou vinculador que gera um arquivo PDB, como \/DEBUG, \/Z7, \/Zd.  Ou \/Zi.  Este segundo arquivo PDB omite os símbolos que você não desejaria enviar aos seus clientes.  Para obter mais informações, consulte [\/PDBSTRIPPED \(remover símbolos privados\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols).|  
|**Gerar arquivo de mapa** \([\/MAP](/visual-cpp/build/reference/map-generate-mapfile)\)|Informe ao vinculador para gerar um arquivo de mapa durante a vinculação.  A configuração padrão é Não.  Para obter mais informações, consulte [\/MAP \(gerar mapfile\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Nome de Arquivo de Mapa** \([\/MAP:](/visual-cpp/build/reference/map-generate-mapfile)*nome*\)|Se você escolher Gerar Arquivo de Mapa, poderá especificar o arquivo de mapa nesta caixa.  Para obter mais informações, consulte [\/MAP \(gerar mapfile\)](/visual-cpp/build/reference/map-generate-mapfile).|  
|**Exportações de Mapa** \([\/MAPINFO:EXPORTS](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Inclui funções exportadas no arquivo de mapa.  A configuração padrão é Não.  Para obter mais informações, consulte [\/MAPINFO \(incluir informações em mapfile\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile).|  
|**Assembly Depurável** \([\/ASSEMBLYDEBUG](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|Especifica configurações para a opção de \/ASSEMBLYDEBUG de vinculador.  Os valores possíveis são os seguintes:<br /><br /> -   **Nenhum atributo debuggable emitido**.<br />-   **Execução de rastreamento e desativação de otimizações \(\/ASSEMBLYDEBUG\)**.  Essa é a configuração padrão,<br />-   **Nenhum acompanhamento em tempo de execução e otimizações habilitadas\(\/ASSEMBLYDEBUG:DISABLE\)**.<br />-   **\<Herdar do pai ou padrões de projeto\>**.<br />-   Para obter mais informações, consulte [\/ASSEMBLYDEBUG \(Adicionar DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute).|  
  
 Você pode alterar essas configurações na pasta Propriedades de Configuração \(categoria Depuração\) programaticamente usando a interface Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings.  Para obter mais informações, consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>.  
  
## Consulte também  
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)   
 [Criando e gerenciando projetos do Visual C\+\+](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)   
 [\/ASSEMBLYDEBUG \(Adicionar DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [Macros comuns para compilar comandos e propriedades](/visual-cpp/ide/common-macros-for-build-commands-and-properties)