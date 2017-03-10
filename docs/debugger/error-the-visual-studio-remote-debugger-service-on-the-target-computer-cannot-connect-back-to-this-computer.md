---
title: "Erro: o servi&#231;o Depurador Remoto do Visual Studio no computador de destino n&#227;o pode se reconectar a este computador | Microsoft Docs"
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
  - "vs.debug.error.service_access_denied_oncallback"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: o servi&#231;o Depurador Remoto do Visual Studio no computador de destino n&#227;o pode se reconectar a este computador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse erro significa que o serviço de depurador remoto do Visual Studio está em execução em uma conta de usuário que não pode autenticar ao tentar se conectar ao computador do qual você está depurando.  
  
 A tabela a seguir mostra quais contas podem acessar o computador:  
  
|||||  
|-|-|-|-|  
||Conta de LocalSystem|Conta de domínio|Contas locais que têm o mesmo nome de usuário e senha nos dois computadores|  
|Ambos os computadores no mesmo domínio|Sim|Sim|Sim|  
|Ambos os computadores em domínios que tenham a confiança bidirecional|Não|Não|Sim|  
|Um ou ambos os computadores em um grupo de trabalho|Não|Não|Sim|  
|Computadores em domínios diferentes|Não|Não|Sim|  
  
 Além disso:  
  
-   A conta na qual você executa o serviço de depurador remoto do Visual Studio deve ser administrador no computador remoto de modo que possa depurar qualquer processo.  
  
-   A conta também tem que ter o privilégio de `Log on as a service` no computador remoto que está usando a ferramenta administrativa **Política de Segurança Local**.  
  
-   Se você estiver usando um acesso de conta local no computador, deverá executar o serviço de depurador remoto do Visual Studio em uma conta local.  
  
### Para corrigir este erro  
  
1.  Verifique se o serviço de depurador remoto do Visual Studio está configurado corretamente no computador remoto.  Para obter mais informações, consulte [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
2.  Execute o serviço de depurador remoto com uma conta que possa acessar o computador host do depurador, conforme mostrado na tabela anterior.  
  
### Para adicionar o privilégio “Fazer logon como um serviço”  
  
1.  No menu **Iniciar**, escolha **Painel de Controle**.  
  
2.  No Painel de Controle, escolha **Exibição Clássica**, se necessário.  
  
3.  Clique duas vezes em **Ferramentas Administrativas**.  
  
4.  Na janela Ferramentas Administrativas, clique duas vezes em **Política de Segurança Local**.  
  
5.  Na janela **Configurações de Segurança Local**, expanda a pasta **Políticas Locais**.  
  
6.  Clique em **Atribuições de Direitos de Usuário**.  
  
7.  Na coluna **Política**, clique duas vezes em **Fazer logon como um serviço** para exibir as atribuições locais atual da Política de Grupo na caixa de diálogo **Fazer logon como um serviço**.  
  
8.  Para adicionar novos usuários, clique no botão **Adicionar Usuário ou Grupo**.  
  
9. Quando terminar de adicionar usuários, clique em **OK**.  
  
### Para resolver esse erro  
  
-   Execute o Monitor de Depuração Remota como um aplicativo em vez de um serviço.  
  
## Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)