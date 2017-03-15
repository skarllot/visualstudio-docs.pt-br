---
title: "Erro: falha no logon remoto do grupo de trabalho | Microsoft Docs"
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
  - "vs.debug.error.workgroup_remote_logon_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "falha de logon, depuração remota"
  - "depuração remota, falha de logon"
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: falha no logon remoto do grupo de trabalho
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este erro é:  
  
 Falha de logon: usuário desconhecido ou senha inválida  
  
 **Causa**  
  
 Esse erro pode ocorrer quando você está depurando de um computador em um grupo de trabalho e tentar se conectar ao computador remoto.  Possíveis causas incluem:  
  
-   Não há nenhuma conta com o nome e a senha correspondentes no computador remoto.  
  
-   Se o computador do Visual Studio e o computador remoto estiverem em grupos de trabalho, esse erro poderá ocorrer devido à configuração padrão de **Política de Segurança Local** no computador remoto.  A configuração padrão de **Política de Segurança Local** é **Convidado somente \- os usuários locais são autenticados como Convidado**.  Para depurar nessa configuração, você deverá alterar a configuração no computador remoto para **Clássico \- os usuários locais são autenticados como eles próprios**.  
  
> [!NOTE]
>  Você deve ser administrador para realizar as seguintes tarefas.  
  
### Para abrir a janela Política de Segurança Local  
  
1.  Inicie o snap\-in **secpol.msc** do Console de Gerenciamento Microsoft \(MMC\).  Digite secpol.msc na pesquisa do Windows, na caixa de execução do Windows ou em um prompt de comando.  
  
### Para adicionar atribuições de direitos de usuário  
  
1.  Abra o local  
  
2.  Abra a janela **Política de Segurança Local**.  
  
3.  Expanda a pasta **Políticas Locais**.  
  
4.  Clique em **Atribuições de Direitos de Usuário**.  
  
5.  Na coluna **Política**, clique duas vezes em **Depurar programas** para exibir as atribuições locais atual da política de grupo na caixa de diálogo **Configuração de Política de Segurança Local**.  
  
     ![Direitos de usuário de diretiva de segurança local](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG\_ERR\_LocalSecurityPolicy\_UserRightsDebugPrograms")  
  
6.  Para adicionar novos usuários, clique no botão **Adicionar Usuário ou Grupo**.  
  
### Para alterar o Modelo de Compartilhamento e Segurança  
  
1.  Abra a janela **Política de Segurança Local**.  
  
2.  Expanda a pasta **Políticas Locais**.  
  
3.  Clique em **Opções de Segurança**.  
  
4.  Na coluna **Política**, clique duas vezes em **Acesso à rede: modelo de compartilhamento e segurança para contas locais**.  
  
5.  Na caixa de diálogo **Acesso à rede: modelo de compartilhamento e segurança para contas locais**, altere o valor para **Clássico \- os usuários locais são autenticados como eles próprios** e clique no botão **Aplicar**.  
  
     ![Opções de segurança de diretiva de segurança local](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG\_ERR\_LocalSecurityPolicy\_SecurityOptions\_NetworkAccess")  
  
## Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)