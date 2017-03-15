---
title: "Anexar aos processos em execu&#231;&#227;o com o Depurador do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.processes.attach"
  - "vs.debug.process"
  - "vs.debug.programs"
  - "vs.debug.detaching"
  - "vs.debug.processes"
  - "vs.debug.error.attach"
  - "vs.debug.remotemachine"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "VB"
  - "c++"
helpviewer_keywords: 
  - "depuração remota, anexando a programas"
  - "processos, anexando a processos em execução"
  - "Caixa de diálogo Anexar ao Processo"
  - "depurando [Visual Studio], anexando a processos"
  - "depurador de processos"
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 57
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anexar aos processos em execu&#231;&#227;o com o Depurador do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Anexando o depurador do Visual Studio para um processo geralmente é útil quando você não tiver iniciado um aplicativo do Visual Studio, mas deseja depurá-lo. Por exemplo, você pode anexar a um processo do IIS ou o serviço do Windows que hospeda um aplicativo .NET. O processo de a que anexar pode ser local ou remoto. Outro exemplo é que se você estiver executando o aplicativo sem o depurador e pressionar uma exceção, você pode, em seguida, anexar ao processo de execução do aplicativo para iniciar a depuração.

Para alguns tipos de aplicativo (como aplicativos da Windows Store), você não conecte diretamente a um nome de processo, mas usar o **Depurar pacote de aplicativos instalado** menu opção (consulte a tabela).

Para ajudá-lo a identificar se você precisa anexar a um processo para seu cenário, alguns dos cenários mais comuns de depuração são mostradas aqui. Onde obter mais instruções estiverem disponíveis, fornecemos links.

|Cenário|Depurar o método|Nome do Processo|Observação e Links|
|-|-|-|-|
|Depurar qualquer tipo de aplicativo com suporte no computador local, iniciando-o no Visual Studio|Padrão de depuração F5|N/D|Consulte [guia de Introdução com o depurador](../debugger/getting-started-with-the-debugger.md)|
|Depuração remota ASP.NET 4 ou 4.5 em um servidor IIS|Usar as ferramentas remotas e anexar ao processo|W3wp.exe|Consulte [ASP.NET de depuração remota em um computador remoto do IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depuração remota principal do ASP.NET em um servidor IIS|Usar as ferramentas remotas e anexar ao processo|dnx.exe|Para implantação de aplicativos, consulte [Publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html). Para depuração, consulte [ASP.NET de depuração remota em um computador remoto do IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Depurar outros tipos de aplicativos com suporte em um processo do servidor|Usar as ferramentas remotas (se o servidor for remoto) e anexar ao processo|Iexplore.exe ou outros processos|Se necessário, use o Gerenciador de tarefas para ajudar a identificar o processo. Consulte [depuração remota](../debugger/remote-debugging.md) e seções posteriores neste tópico|
|Depurar remotamente um aplicativo de área de trabalho do Windows|F5 e as ferramentas remotas|N/D| Consulte [depuração remota](../debugger/remote-debugging.md)|
|Um aplicativo Windows Universal (UWP), OneCore, HoloLens ou IoT de depuração remota|Depurar o pacote de aplicativo instalado|N/D|Use **Debug / outros destinos de depuração / depurar o pacote de aplicativos instalados** em vez de **anexar ao processo**|
|Depurar um aplicativo Windows Universal (UWP), OneCore, HoloLens ou IoT que não foi iniciado no Visual Studio|Depurar o pacote de aplicativo instalado|N/D|Use **Debug / outros destinos de depuração / depurar o pacote de aplicativos instalados** em vez de **anexar ao processo**|
  
> [!WARNING]
>  Para anexar a um aplicativo Windows Universal que é escrito em JavaScript, você deve primeiro habilitar a depuração para o aplicativo. Consulte [anexar o depurador](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) no Centro de desenvolvimento do Windows.  
  
> [!NOTE]
>  Para que o depurador se anexe ao código escrito em C++, o código precisa emitir `DebuggableAttribute`. Você pode adicionar isso ao seu código automaticamente por meio da vinculação com o [/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) opção de vinculador.

## <a name="what-debugger-features-can-i-use"></a>Quais recursos do depurador podem usar?

Para usar os recursos completos do depurador do Visual Studio (como usar pontos de interrupção), o executável deve corresponder exatamente ao seu local de origem e símbolos (ou seja, o depurador deve ser capaz de carregar o correto [(.pbd) arquivos de símbolo](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Por padrão, isso requer uma compilação de depuração.

Para cenários de depuração remota, você deve ter o código-fonte uma cópia do código-fonte estiver aberto no Visual Studio. Os binários do aplicativo compilado no computador remoto devem vir da mesma compilação como na máquina local.

Em alguns cenários de depuração locais, você pode depurar no Visual Studio sem acesso à fonte de se os arquivos de símbolos corretos estão presentes com o aplicativo (por padrão, isso requer uma compilação de depuração). Para obter mais informações, consulte [especificar símbolo e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Para aplicativos de desktop do Windows, você também pode depurar o aplicativo em execução usando o depurador JIT (Visual Studio abre e você entrar no código do aplicativo após a ocorrência de um erro).

##  <a name="a-namebkmkattachtoaprocessonaremotecomputera-attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Anexar a um processo em um computador remoto  
 Para anexar a um processo, você deve saber o nome do processo. Para aplicativos ASP.NET que foram implantados no IIS, consulte [ASP.NET de depuração remota em um computador remoto do IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou [Publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html) para aplicativos ASP.NET Core. Para outros aplicativos, você poderá localizar o nome do processo no Gerenciador de tarefas.
  
 Quando você usa o **anexar ao processo** caixa de diálogo, você pode selecionar outro computador que foi configurado para depuração remota. Para obter mais informações, consulte [depuração remota](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md). Quando você tiver selecionado um computador remoto, poderá exibir uma lista de processos disponíveis que estão em execução no computador e anexá-la a um ou mais processos para depuração.
  
 **Para selecionar um computador remoto:**  

1. No Visual Studio, selecione **Depurar / anexar a processo**.

2.  No **anexar ao processo** caixa de diálogo, selecione a conexão adequada digitar do **Transporte** lista. **Padrão** é a configuração correta para a maioria dos casos.

    O **Transporte** configuração persiste entre sessões de depuração. 
  
3.  Use o **qualificador** caixa de listagem para escolher o nome do computador remoto por um dos seguintes métodos:  
  
    1.  Digite o nome no **qualificador** caixa de listagem.
    
        >**Observação** se, em etapas posteriores, você não pode se conectar usando o nome do computador remoto, use o endereço IP. (O número da porta pode aparecer automaticamente depois de selecionar o processo. Você também pode inseri-lo manualmente. Na ilustração abaixo, 4020 é a porta padrão para o depurador remoto.)  
  
    2.  Clique na seta suspensa anexada para o **qualificador** caixa da lista e selecione o nome do computador na lista suspensa.  
  
    3.  Clique o **localizar** próximo ao**qualificador** lista para abrir o **Selecionar conexão de depurador remoto** caixa de diálogo. O **Selecionar conexão de depurador remoto** caixa de diálogo lista todos os dispositivos que estão em sua sub-rede local e qualquer dispositivo que está conectado diretamente ao computador por um cabo Ethernet. Clique no computador ou dispositivo que você deseja e, em seguida, clique em **selecionar**. 
    
    ![DBG_Basics_Attach_To_Process](../debugger/media/dbg_basics_attach_to_process.png "DBG_Basics_Attach_To_Process") 
  
     O **qualificador** configuração persiste entre sessões de depuração somente se uma conexão de depuração bem-sucedida ocorre com o qualificador.
     
4.  Clique em **atualizar**.

      O **processos disponíveis** lista é exibida automaticamente quando você abre o **processos** caixa de diálogo. Os processos podem iniciar e parar em segundo plano quando a caixa de diálogo está aberta. No entanto, o conteúdo nem sempre será atual. Você pode atualizar a lista a qualquer momento para ver a lista atual de processos clicando **atualizar**. 
     
4.  No **anexar ao processo** caixa de diálogo caixa, localize o programa que você deseja anexar o **processos disponíveis** lista.  
  
     Se o processo é executado em uma conta de usuário diferente, selecione o **Mostrar processos de todos os usuários** caixa de seleção.
     
5.  Clique em **anexar**.  
  
##  <a name="a-namebkmkattachtoarunningprocessa-attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Anexar a um processo em execução na máquina local  
 Para anexar a um processo, você deve saber o nome do processo.  Você poderá localizar o nome do processo no Gerenciador de tarefas.  
  
1.  No Visual Studio, selecione **Depurar / anexar a processo**.
  
2.  No **anexar ao processo** caixa de diálogo caixa, localize o programa que você deseja anexar o **processos disponíveis** lista.  
  
     Se o processo é executado em uma conta de usuário diferente, selecione o **Mostrar processos de todos os usuários** caixa de seleção.
  
3.  No **anexar a** caixa, certifique-se de que o tipo de código que você irá depurar está listado. O padrão **automáticas** configuração tenta determinar que tipo de código que você deseja depurar. Para definir o tipo de código manualmente, faça o seguinte  
  
    1.  No **anexar a** clique em **selecionar**.  
  
    2.  Na **Select Code Type** caixa de diálogo, clique em **Depurar esses tipos de código** e selecione os tipos para depurar.  
  
    3.  Clique em **OK**.  
  
4.  Clique em **anexar**.

## <a name="additional-info"></a>Informações adicionais

Você pode estar associado a vários programas enquanto depura, mas somente um programa está ativo no depurador em um determinado momento. Você pode definir o programa ativo no **local de depuração** barra de ferramentas ou **processos** janela. Para obter mais informações, consulte [como: definir o programa atual](http://msdn.microsoft.com/pt-br/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
Se você tentar anexar a um processo de propriedade de uma conta de usuário não confiável, aparecerá uma confirmação da caixa de diálogo de aviso de segurança. Para obter mais informações, consulte [Aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir pareçam suspeitas ou você não tiver certeza, não anexe a esse processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
Em alguns casos, quando você depura em uma sessão de área de trabalho remota (serviços de Terminal), o **processos disponíveis** lista não exibirá todos os processos disponíveis. Se você estiver executando o Visual Studio como um usuário que tenha uma conta de usuário limitado, o **processos disponíveis** lista não mostrará processos em execução na sessão 0, que é usada para serviços e outros processos do servidor, incluindo w3wp.exe. Você pode resolver o problema executando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] em uma conta de administrador ou executando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no console do servidor em vez de uma sessão de Serviços de Terminal. Se nenhuma dessas soluções alternativas for possível, uma terceira opção é anexar ao processo executando `vsjitdebugger.exe -p` *ProcessId* na linha de comando do Windows. Você pode determinar a ID do processo usando tlist.exe. Para obter tlist.exe, baixe e instale as ferramentas de depuração para Windows, disponível em  [downloads WDK e WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).
  
##  <a name="a-namebkmktroubleshootattacherrorsa-troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Solucionar problemas de erros de anexo  
 Quando o depurador é anexado a um processo em execução, o processo pode conter um ou mais tipos de código. Os tipos de código, o depurador pode anexar são exibidos e selecionados na **Select Code Type** caixa de diálogo.  
  
 Às vezes, o depurador pode ser anexado com êxito a um tipo de código, mas não a outro tipo de código. Isso pode ocorrer se você estiver tentando anexar a um processo que esteja sendo executado em um computador remoto. O computador remoto pode ter componentes de depuração remota instalados para alguns tipos de código mas não para outros. Isso também pode ocorrer se você tentar anexar a dois ou mais processos para depuração direta de banco de dados. A depuração de SQL dá suporte à anexação de apenas um único processo.  
  
 Se o depurador puder se conectar a alguns, mas não a todos os tipos de código, você verá uma mensagem identificando quais tipos não conseguiram estabelecer conexão.  
  
 Se o depurador for anexado com êxito a pelo menos um tipo de código, você poderá depurar o processo. Você poderá depurar apenas os tipos de código que foram anexados com êxito. A mensagem do exemplo anterior mostra que o tipo de código de script não foi anexado. Portanto, você não pode depurar o código do script dentro do processo. O código de script no processo ainda seria executado, mas você não poderia definir pontos de interrupção, exibir dados ou executar outras operações de depuração no script.  
  
 Se você desejar informações mais específicas sobre por que o depurador não foi anexado a um tipo de código, tente reanexar somente àquele tipo de código.  
  
 **Para obter informações específicas sobre por que um tipo de código falha ao anexar**  
  
1.  Desanexe do processo. Sobre o **Depurar** menu, clique em **Desanexar tudo**.  
  
2.  Anexe o processo novamente, selecionando apenas um único tipo de código.  
  
    1.  No **anexar ao processo** caixa de diálogo, selecione o processo no **processos disponíveis** lista.  
  
    2.  Clique em **selecionar**.  
  
    3.  Na **Select Code Type** caixa de diálogo, selecione **Depurar esses tipos de código** e o tipo de código que não foi anexado. Limpe qualquer outro código.  
  
    4.  Clique em **OK**. O **Select Code Type** caixa de diálogo é fechada.  
  
    5.  No **anexar ao processo** caixa de diálogo, clique em **Attach**.  
  
     Desta vez, o anexo falhará completamente e você receberá uma mensagem de erro específica.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar vários processos](../debugger/debug-multiple-processes.md)   
 [Depuração Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Depuração remota](../debugger/remote-debugging.md)