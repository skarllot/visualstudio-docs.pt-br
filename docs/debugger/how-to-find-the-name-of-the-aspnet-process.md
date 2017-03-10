---
title: "Como localizar o nome do processo ASP.NET | Microsoft Docs"
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
  - "depuração do ASP.NET, processo do ASP.NET"
  - "processo do ASP.NET"
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como localizar o nome do processo ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para anexar a um aplicativo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] em execução, você precisará saber o nome do processo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  
  
-   Se estiver executando o IIS 6.0 ou IIS 7.0, o nome será w3wp.exe.  
  
-   Se estiver executando uma versão anterior do IIS, o nome será aspnet\_wp.exe.  
  
 Para os aplicativos criados usando o [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] ou versões posteriores, o código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pode residir no sistema de arquivos e ser executado no servidor de teste WebDev.WebServer.exe.  Nesse caso, você deve anexar a WebDev.WebServer.exe em vez do processo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Essa situação aplica\-se somente à depuração local.  
  
 Aplicativos ASP antigos são executados dentro do processo inetinfo.exe do IIS quando ele está sendo executado no processo.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.  Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para determinar se o código de projeto reside no sistema de arquivos ou IIS  
  
1.  No Visual Studio, abra o **Gerenciador de Soluções** se já não estiver aberto.  
  
2.  Selecione o nó superior que contém o nome do aplicativo.  
  
3.  Se o título da janela **Propriedades** contiver um caminho de arquivo, o código do aplicativo residirá no sistema de arquivos.  
  
     Caso contrário, o título da janela **Propriedades** conterá o nome do site.  
  
### Para determinar a versão do IIS no qual o aplicativo está sendo executado  
  
1.  Localize **Ferramentas Administrativas** e execute\-as.  Dependendo do sistema operacional, pode ser um ícone dentro de **Painel de Controle** ou uma entrada de menu que aparece quando você clica em **Iniciar**.  
  
     No Windows XP, o **Painel de Controle** pode estar na Exibição por Categoria ou na Exibição Clássica.  Na Exibição por Categoria, é necessário clicar em **Alternar para o Modo de Exibição Clássico** ou **Desempenho e Manutenção** para ver o ícone de **Ferramentas Administrativas**.  
  
2.  Em **Ferramentas Administrativas**, execute Serviços de Informações da Internet.  Uma caixa de diálogo do MMC é exibida.  
  
3.  Se houver mais de um computador listado no painel esquerdo, selecione o computador no qual o código do aplicativo reside.  
  
4.  A versão do IIS está na coluna **Versão** do painel direito.  
  
## Consulte também  
 [Pré\-requisitos para aplicativos Web de depuração remota](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Preparando\-se para depurar ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Depurando aplicativos Web e script](../debugger/debugging-web-applications-and-script.md)