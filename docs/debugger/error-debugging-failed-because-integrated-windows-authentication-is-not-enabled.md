---
title: "Erro: falha na depura&#231;&#227;o porque a autentica&#231;&#227;o integrada do Windows n&#227;o est&#225; habilitada | Microsoft Docs"
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
  - "vs.debug.error.webdbg_ntlm_authn_not_enabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "depurador, erros de aplicativo Web"
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: falha na depura&#231;&#227;o porque a autentica&#231;&#227;o integrada do Windows n&#227;o est&#225; habilitada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A autenticação do usuário que solicitou a depuração foi impedida por um erro de autenticação.  Isso pode ocorrer ao tentar entrar em um aplicativo Web ou serviço Web XML.  Uma causa desse erro é que a autenticação integrada do Windows não está habilitada.  Para habilitá\-la, siga as etapas em “Para habilitar a autenticação integrada do Windows”.  
  
 Se você tiver habilitado a autenticação integrada do Windows e esse erro ainda aparecer, é possível que este erro seja causado porque **Autenticação Digest para servidores de domínio do Windows** está habilitado.  Nessa situação, você deverá entrar em contato com o administrador da rede.  
  
### Para habilitar a autenticação integrada do Windows  
  
1.  Faça logon no servidor Web com uma conta de administrador.  
  
2.  Clique em **Iniciar** e em **Painel de Controle**.  
  
3.  No **Painel de Controle**, clique duas vezes em **Ferramentas de Administração**.  
  
4.  Clique duas vezes em **Serviços de Informações da Internet**.  
  
5.  Clique no nó do servidor Web.  
  
     Uma pasta **Sites** é aberta abaixo do nome do servidor.  
  
6.  Você pode configurar a autenticação para todos os sites ou para sites individuais.  Para configurar a autenticação para todos os sites, clique com o botão direito na pasta **Sites** e clique em **Propriedades**.  Para configurar a autenticação para um site individual, abra a pasta **Sites**, clique com o botão direito no site individual e clique em **Propriedades**.  
  
     A caixa de diálogo **Propriedades** é exibida.  
  
7.  Clique em **Segurança de Diretório**.  
  
8.  Na seção **Acesso anônimo e controle de autenticação**, clique em **Editar**.  
  
     A caixa de diálogo **Métodos de Autenticação** é exibida.  
  
9. Em **Acesso autenticado**, selecione **Autenticação integrada do Windows**.  
  
10. Clique em **OK** para fechar a caixa de diálogo **Métodos de Autenticação**.  
  
11. Clique em **OK** para fechar a caixa de diálogo **Propriedades**.  
  
12. Feche a janela **Serviços de Informações da Internet**.  
  
### Para habilitar a autenticação integrada do Windows no Windows Vista\/IIS 7  
  
1.  Faça logon no servidor Web com uma conta de administrador.  
  
2.  Ative a Autenticação do Windows e a Compatibilidade de Gerenciamento do II6, se você ainda não tiver feito isso anteriormente, seguindo estas etapas:  
  
    1.  Clique em **Iniciar**, clique em **Painel de Controle** e em **Programas**.  
  
    2.  Em **Programas e Recursos**, clique em **Ativar ou Desativar Recursos do Windows**.  
  
         A caixa de diálogo Controle de Acesso do Usuário aparecerá e solicitará para que a permissão continue.  
  
    3.  Clique em **Continuar**.  
  
         A caixa de diálogo Recursos do Windows é exibida.  
  
    4.  Na lista de recursos, expanda o nó **Serviços de Informações da Internet**.  
  
    5.  Em **Serviços de Informações da Internet**, expanda o nó **Serviços da World Wide Web**.  
  
    6.  Em **Serviços da World Wide Web**, clique em **Segurança**.  
  
    7.  Clique em **Autenticação do Windows**.  
  
    8.  Em **Serviços de Informações da Internet**, expanda o nó **Ferramentas de Gerenciamento da Web**.  
  
    9. Expanda **Ferramentas de Gerenciamento da Web**, expanda o nó **Gerenciamento de compatibilidade do IIS 6** e selecione a caixa de seleção **Compatibilidade da Configuração da Metabase do IIS 6**.  
  
    10. Em **Ferramentas de Gerenciamento da Web**, selecione **Console de Gerenciamento do IIS** e clique em **OK.**  
  
    11. Reinicie o computador para que essas alterações tenham efeito.  
  
3.  Clique em **Iniciar** e em **Painel de Controle**.  
  
4.  Clique em **Exibição clássica** e clique duas vezes em **Ferramentas Administrativas**.  
  
5.  Na coluna **Nome** e clique duas vezes em **Gerenciador do IIS \(Serviços de Informações da Internet\)**.  
  
6.  Na coluna **Conexões**, expanda o nó para o servidor.  
  
     Uma pasta **Sites** é aberta abaixo do nome do servidor.  
  
7.  Expanda o nó **Sites** e clique no site para a qual você deseja habilitar a autenticação integrada do Windows.  
  
8.  O título do painel central altera o nome do site que você selecionou.  Neste painel, no título **IIS**, clique duas vezes em **Autenticação**.  
  
     O título do painel é alterado para **Autenticação**.  
  
9. No painel **Autenticação**, na coluna **Nome**, clique com o botão direito em **Autenticação do Windows** e clique em **Habilitar**.  
  
10. Feche a janela **Gerenciador do IIS \(Serviços de Informações da Internet\)**.  
  
## Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Autenticação Digest da Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Running Web Applications on Windows Vista with IIS 7.0 and Visual Studio](../Topic/Running%20Web%20Applications%20on%20Windows%20Vista%20with%20IIS%207.0%20and%20Visual%20Studio.md)