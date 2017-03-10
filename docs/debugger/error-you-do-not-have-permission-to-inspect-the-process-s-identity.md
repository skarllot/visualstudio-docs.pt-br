---
title: "Erro: voc&#234; n&#227;o tem permiss&#227;o para inspecionar a identidade do processo | Microsoft Docs"
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
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: voc&#234; n&#227;o tem permiss&#227;o para inspecionar a identidade do processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você não tem permissão para inspecionar a identidade do processo.Isto pode ocorrer devido à configuração do sistema.  
  
 O depurador não pôde inspecionar a identidade do processo, que são informações necessárias para depuração.  A causa mais provável é que os Serviços de Terminal estão sendo desabilitados.  O serviço dos Serviços de Terminal é habilitado por padrão.  Siga estas etapas para habilitá\-lo novamente.  
  
### Para habilitar Serviços de Terminal  
  
1.  Clique em **Iniciar** e escolha **Painel de Controle**.  
  
2.  No Painel de Controle, escolha **Alternar para o Modo de Exibição Clássico**, se necessário, e clique duas vezes em **Ferramentas Administrativas**.  
  
3.  Na janela **Ferramentas Administrativas**, clique duas vezes em **Gerenciamento de Computador**.  
  
4.  Na janela Gerenciamento de Computador, expanda o nó **Serviços e Aplicativos**.  
  
5.  Em **Serviços e Aplicativos**, clique em **Serviços**.  
  
     Uma lista de serviços aparece no painel direito.  
  
6.  Na lista **Serviços**, clique com o botão direito em **Serviços de Terminal** e escolha **Propriedades**.  
  
7.  Na janela **Propriedades dos Serviços de Terminal**, vá para a guia **Geral** e defina o **Tipo de Inicialização** como **Manual**.  
  
8.  Clique em **OK**.  
  
9. Reinicie o computador.  
  
     Esse procedimento não habilita automaticamente a Área de Trabalho Remota.  Se quiser habilitar a Área de Trabalho Remota no computador, execute o seguinte procedimento adicional.  
  
### Para habilitar a Área de Trabalho Remota  
  
1.  Clique em **Iniciar** e clique com o botão direito em **Meu Computador**.  
  
2.  Escolha **Propriedades**.  
  
     A janela **Propriedades do Sistema** é exibida.  
  
3.  Clique em **Remoto**.  
  
4.  Em **Área de Trabalho Remota**, selecione **Permitir que usuários se conectem remotamente a este computador**.  
  
5.  Clique em **OK**.  
  
## Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)