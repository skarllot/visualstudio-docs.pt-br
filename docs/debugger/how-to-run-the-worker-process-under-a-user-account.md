---
title: "Como executar o processo de trabalho em uma conta de usu&#225;rio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
helpviewer_keywords: 
  - "contas de usuário, aspnet_wp.exe"
  - "Depuração de aplicativos da Web do ASP.NET"
  - "ferramentas, aspnet_wp.exe"
  - "ASP.NET, ferramentas"
  - "aspnet_wp.exe"
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como executar o processo de trabalho em uma conta de usu&#225;rio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para configurar o computador de modo que você possa executar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (aspnet_wp.exe ou w3wp.exe) em uma conta de usuário, siga estas etapas.  
  
## <a name="procedure"></a>Procedimento  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Para executar aspnet_wp.exe em uma conta de usuário  
  
1.  Abra o arquivo machine.config, localizado no computador na pasta CONFIGURATION no caminho onde você instalou o tempo de execução.  
  
2.  Encontre o &lt;processModel&gt; seção e alterar os atributos de usuário e senha para o nome e a senha da conta de usuário que você deseja aspnet_wp.exe para ser executado em.  
  
3.  Salve o arquivo machine.config.  
  
4.  No [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)], o IIS 6.0 está instalado por padrão. O processo de trabalho correspondente é w3wp.exe. Para executar no modo do IIS 6.0 com o aspnet_wp.exe como o processo de trabalho, siga estas etapas:  
  
    1.  Clique em **Iniciar**, clique em **Ferramentas administrativas** e, em seguida, escolha **Serviços de informações da Internet**.  
  
    2.  No **Internet Information Services** caixa de diálogo, clique o **Sites da Web** pasta e escolha **propriedades**.  
  
    3.  No **Propriedades de Sites da Web** caixa de diálogo, escolha **serviço**.  
  
    4.  Selecione **Executar serviço WWW no modo de isolamento do IIS 6.0**.  
  
    5.  Feche o **propriedades** caixa de diálogo e **Gerenciador de serviços de Internet**.  
  
5.  Abra um prompt de comando do Windows e redefina o servidor executando:  
  
    ```  
    iisreset  
    ```  
    – ou –  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  Localize a pasta de arquivos temporários do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], que deve estar no mesmo caminho que a pasta CONFIG. Clique com botão direito temporárias [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] arquivos de pasta e escolha **propriedades** no menu de atalho.  
  
7.  No **Propriedades de arquivos temporários do ASP.NET** caixa de diálogo, clique o **segurança** guia.  
  
8.  Clique em **avançada**.  
  
9. No **configurações de segurança avançadas para arquivos temporários do ASP.Net** caixa de diálogo, clique em **Add**.  
  
    O **caixa de diálogo Selecionar usuário, computador ou grupo** é exibida.  
  
10. Digite o nome de usuário na **Insira o nome do objeto para selecionar** caixa e, em seguida, clique em **OK**. O nome de usuário deve seguir este formato: NomedeDomínio\NomedeUsuário.  
  
11. No **entrada de permissão para arquivos temporários do ASP.NET** caixa de diálogo caixa, dê ao usuário **controle total**, e, em seguida, clique em **OK** para fechar o **entrada para arquivos temporários do ASP.NET** caixa de diálogo.  
  
12. Um **segurança** caixa de diálogo será exibida e perguntará se você realmente quer alterar as permissões em uma pasta do sistema. Clique em **Sim**.  
  
13. Clique em **OK** para fechar o **Propriedades de arquivos temporários do ASP.NET** caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
[Depuração do ASP.NET: Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md)  
  
