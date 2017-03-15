---
title: "Erro: n&#227;o foi poss&#237;vel iniciar a depura&#231;&#227;o no servidor Web | Microsoft Docs"
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
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, erros de aplicativo Web"
  - "depurando [Visual Studio], erros"
  - "depurando aplicativos Web ASP.NET, erro não é possível iniciar a depuração"
  - "erros [depurador], não é possível iniciar a depuração"
  - "servidores HTTP, depurando erro"
  - "IIS, depurando DLLs"
  - "depuração remota, erros"
  - "segurança [depurador], aplicativos da Web"
  - "configurações de segurança, verificando sites padrão"
  - "erro não é possível iniciar a depuração"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: n&#227;o foi poss&#237;vel iniciar a depura&#231;&#227;o no servidor Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você tenta depurar um aplicativo ASP.NET em execução em um servidor Web, você pode receber essa mensagem de erro: não é possível iniciar a depuração no servidor Web.  
  
 Na maioria dos casos, esse erro ocorre porque o IIS não está configurado corretamente.  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> Verifique se o que IIS está configurado corretamente  
 Para obter informações sobre como implantar o IIS 8 com um aplicativo MVC 5, consulte [Publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Para obter informações sobre a implantação em IIS7.5, consulte [Depuração ASP.NET em um servidor remoto 7.5 remota do computador](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> Verifique se que as ferramentas remotas do Visual Studio estão instaladas  
 Se você está tentando depurar em um servidor Web remoto, as ferramentas remotas do Visual Studio deve ser instaladas. Para obter informações sobre como baixar e instalar as ferramentas remotas, consulte [Depuração remota](../debugger/remote-debugging.md).  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> Verifique se que o ASP.NET está instalado  
 **IIS 8**  
  
 Para o IIS 8, você instala o ASP.NET como parte do IIS.  
  
1.  No **Gerenciador de servidores** lado a lado, selecione **painel**, e clique em **Adicionar funções e recursos**.  
  
2.  Sobre o **tipo de instalação** página, selecione **instalação baseada em função ou recurso**, e clique em **próximo**.  
  
3.  Sobre o **servidor de destino** selecione **Selecione um servidor no pool de servidores**, selecione seu servidor e clique em **próximo**.  
  
4.  Sobre o **Selecionar funções de servidor** selecione **servidor Web \(IIS\)**, e clique em **próximo**.  
  
5.  Sobre o **página Selecionar recursos**, clique em **próximo**.  
  
6.  Sobre o **função de servidor Web \(IIS\)** clique em **próximo**.  
  
7.  No **Selecionar Serviços de função** página, observe os serviços de função pré\-selecionados que são instalados por padrão, expanda o **Application Server** nó, o **.NET Framework 4.5** nó e selecione **ASP.NET 4.5**. \(Se você instalou o .NET 3.5, selecione **ASP.NET 3.5** também.\)  
  
8.  Sobre o **Confirmar seleções de instalação** clique em **instalar**.  
  
9. Sobre o **progresso da instalação** página, confirme que a instalação do função do servidor Web \(IIS\) e serviços de função necessários foi concluída com êxito e, em seguida, clique em **Fechar**.  
  
 **IIS 7.5 e versões anterior**  
  
 Para o IIS 7.5 e versões anteriores: em uma janela de prompt de comando, execute o seguinte comando:  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## Solução de problemas básicos  
 Aqui estão algumas coisas que você pode fazer para certificar\-se de que seu aplicativo ASP.NET é implantado corretamente.  
  
## Abrir a página de localhost no navegador  
 Se o IIS não está instalado corretamente, você verá erros quando você digita `http://localhost` em um navegador.  
  
## Abrir a página da Web no navegador  
 Inicie um navegador da Web e digite a URL da página que você está tentando depurar \(por exemplo: `http://localhost/MyWebApplication`\). Se o IIS não está configurado corretamente ou seu aplicativo ASP.NET não está implantado corretamente, você deve obter erros que ajudam você a corrigir a instalação do IIS e implantação do ASP.NET.  
  
## Criar um aplicativo básico do ASP.NET no servidor  
 Tente criar um aplicativo básico ASP.NET localmente no servidor e tente depurá\-lo.  
  
## Resolver erros de autenticação, se você estiver usando somente o endereço IP  
 Por padrão, endereços IP são considerados como parte da Internet e a autenticação NTLM não é feita pela Internet. Se seu site estiver configurado no IIS para exigir autenticação, essa autenticação falhará. Para corrigir esse problema, você pode especificar o nome do computador remoto.  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> Anexar manualmente ao processo  
 Se você ainda receber uma mensagem de erro ao iniciar a depuração, convém tentar depurar o aplicativo anexando manualmente ao processo.  
  
-   Inicie o aplicativo sem depuração. \(Da **Depurar** menu, escolha **Start Without Debugging**.\)  
  
-   Clique em **Debug\/anexar a processo**.  Quando a janela for exibida, habilitar **Mostrar processos de todos os usuários**.  
  
-   Localize o processo apropriado e anexar a ele. Para aplicativos ASP.NET antes do MVC 5, o processo é w3wp.exe. Para o MVC 5, consulte [Publicar no IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
## Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)