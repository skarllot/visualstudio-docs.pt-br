---
title: "Erro: o Monitor de Depura&#231;&#227;o Remota do Microsoft Visual Studio (MSVSMON.EXE) parece n&#227;o estar sendo executado no computador remoto. | Microsoft Docs"
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
  - "vs.debug.error.server_machine_no_default"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: o Monitor de Depura&#231;&#227;o Remota do Microsoft Visual Studio (MSVSMON.EXE) parece n&#227;o estar sendo executado no computador remoto.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa mensagem de erro significa que o Visual Studio não pôde localizar a instância correta do Visual Studio Monitor de depuração remota no computador remoto. O Visual Studio Monitor de depuração remota deve estar instalado para depuração remota funcione. Para obter informações sobre como baixar e configurar o depurador remoto, consulte [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
> [!IMPORTANT]
>  Se você acredita ter recebido esta mensagem por causa de um bug no produto, relate esse problema ao Visual Studio [Enviar um Smiley](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md). Se você precisar de mais ajuda, consulte [Fale conosco](../ide/talk-to-us.md) para obter formas de contatar a Microsoft.  
  
## Recebi a seguinte mensagem enquanto eu estava depurando no Visual Studio 2010 ou anterior  
 Se a versão do Visual Studio que você estiver usando o Visual Studio 2010 ou anterior, você também poderá receber esse erro se o compartilhamento de arquivo e impressora não está habilitado. Para obter mais informações sobre esse problema, consulte a versão do Visual Studio 2010 desta documentação: [erro: O Microsoft Visual Studio Monitor de depuração remota \(MSVSMON. EXE\) não parece estar em execução no computador remoto. \-Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## Recebi a seguinte mensagem enquanto eu estava depurando localmente  
 Se você estiver recebendo essa mensagem enquanto você estiver depurando localmente, o software antivírus ou um firewall de terceiros pode ser culpado. Visual Studio é um aplicativo de 32 bits, portanto, ele usa a versão de 64 bits do depurador remoto para depurar aplicativos de 64 bits. Os dois processos se comunicar usando a rede local no computador local. Nenhum tráfego deixa o computador, mas é possível que o software de segurança de terceiros pode bloquear a comunicação.  
  
 As seções a seguir listam alguns outros motivos por que você talvez tenha essa mensagem e o que você pode fazer para corrigir o problema.  
  
## O computador remoto não está acessível  
 Tente [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) a máquina remota. Se ele não responder ao ping, as ferramentas remotas não poderá se conectar. Tente reiniciar a máquina remota e caso contrário, certificando\-se de que ele está configurado corretamente na rede.  
  
## A versão do depurador remoto não corresponde à versão do Visual Studio  
 A versão do Visual Studio que você está executando localmente precisa corresponder à versão do monitor de depuração remota em execução no computador remoto. Para corrigir esse problema, baixe e instale a versão correspondente do monitor de depuração remota. Vá para o [Centro de Download](http://www.microsoft.com/en-us/download) para localizar a versão correta do depurador remoto.  
  
## As máquinas locais e remotas têm diferentes modos de autenticação  
 As máquinas locais e remotas precisam usar o mesmo modo de autenticação. Para corrigir esse problema, certifique\-se de que ambos os computadores estão usando o mesmo modo de autenticação. Para obter mais informações sobre modos de autenticação, consulte [Visão geral sobre a autenticação do Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## O depurador remoto é executado sob uma conta de usuário diferente  
 Você pode resolver isso em uma das seguintes maneiras:  
  
-   Você pode parar o depurador remoto e reiniciá\-lo com a conta que você está usando no computador local.  
  
-   Você pode iniciar o depurador remoto na linha de comando com o **\/Allow \< username \>** parâmetro: `msvsmon /allow <username@computer>`  
  
-   Você pode adicionar o usuário com permissões do depurador remoto \(na janela do depurador remoto, **Ferramentas \/ permissões**\).  
  
-   Se você não pode usar os métodos nas etapas anteriores, você pode permitir que qualquer usuário pode fazer a depuração remota. Na janela do depurador remoto, vá para o **\/Opções de ferramentas** caixa de diálogo. Quando você seleciona   **sem autenticação**, em seguida, você pode verificar **Permitir que qualquer usuário depure**. No entanto, você deve usar essa opção somente se você não tem escolha, ou se você estiver em uma rede privada.  
  
## O firewall na máquina remota não permite conexões de entrada para o depurador remoto  
 O firewall no computador do Visual Studio e o firewall no computador remoto devem ser configurados para permitir a comunicação entre o Visual Studio e o depurador remoto. Para obter informações sobre as portas que o depurador remoto está usando, consulte [Atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md). Para obter informações sobre como configurar o firewall do Windows, consulte [Configurar o Firewall do Windows para a depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## O software antivírus está bloqueando as conexões  
 Software de antivírus do Windows permite conexões de depurador remoto, mas alguns softwares antivírus de terceiros podem bloqueá\-los. Verifique a documentação do seu software antivírus saber como permitir que essas conexões.  
  
## Política de segurança de rede está bloqueando a comunicação entre o computador remoto e o Visual Studio  
 Examine a segurança da rede para certificar\-se de que ele não está bloqueando a comunicação. Para obter mais informações sobre a política de segurança de rede do Windows, consulte [gerenciamento de segurança](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## A rede está muito ocupada para dar suporte à depuração remota  
 Talvez seja necessário fazer a depuração remota em um momento diferente ou reagendar o trabalho na rede para um horário diferente.  
  
## Mais ajuda  
 Para obter ajuda de depurador mais remota, incluindo opções de linha de comando, clique em **Ajuda \/ uso** na janela do depurador remoto. Se você não estiver com ele aberto você pode ver a página da web, copie a seguinte linha para um  **File Explorer** janela. \(Você precisa substituir \< diretório de instalação do Visual Studio \> com o local de instalação do Visual Studio.\)  
  
 res: \/ \/*\< diretório de instalação do Visual Studio \>*\\Common7\\IDE\\Remote%20Debugger\\x64\\msvsmon.exe\/help.htm  
  
## Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)