---
title: "Depura&#231;&#227;o de script do lado do cliente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "depuração [Visual Studio], scripts do lado do cliente"
  - "scripts do lado do cliente, depuração"
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depura&#231;&#227;o de script do lado do cliente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O depurador do Visual Studio fornece um ambiente de depuração completo para localizar e corrigir erros em scripts de cliente em páginas ASP.NET.  
  
## Abrindo documentos de Script  
 Você pode ver a lista de documentos de script do lado do servidor e cliente no **Solution Explorer** para exibir. Você pode abrir qualquer documento de script do **Solution Explorer**. Para obter mais informações, consulte [Como exibir documentos de script](../debugger/how-to-view-script-documents.md).  
  
## Mapeamento de ponto de interrupção  
 No Visual Studio, você não pode depurar diretamente o código do lado do servidor, mas você pode definir um ponto de interrupção em um arquivo no servidor. Visual Studio automaticamente mapeia o ponto de interrupção em um local correspondente no arquivo do lado do cliente e cria um ponto de interrupção mapeado no código do lado do cliente.  
  
## Anexando manualmente ou automaticamente ao Script  
 Para iniciar a depuração de script no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], o depurador deve anexar o script que você deseja depurar. Isso pode acontecer manualmente ou automaticamente.  
  
 Você pode anexar manualmente usando o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interface do depurador para escolher um processo em execução de script que deseja anexar. Para obter mais informações, consulte [Como anexar ao script](../debugger/how-to-attach-to-script.md).  
  
 O depurador é anexado automaticamente ao script quando ocorre um dos seguintes itens:  
  
-   Você atinge um ponto de interrupção no script.  
  
-   Clicar em um VBScript `Stop` instrução ou JScript `debugger` instrução no seu código de script.  
  
-   O navegador ou o servidor encontra uma sintaxe ou executado erros de tempo em seu script. Quando isso ocorre, uma caixa de diálogo é exibida e tem a opção de iniciar a depuração.  
  
 Quando você anexa manualmente ao script, o processo de script continua a executar até que ele é paralisado de alguma maneira. Você pode interromper escolhendo **quebra** no **Depurar** menu.  
  
 Quando o depurador é anexado automaticamente, a execução do script é interrompida na linha onde o ponto de interrupção `Stop` instrução ou `debugger` ou erro ocorreu, ou no ponto onde você optou por iniciar a depuração no Internet Explorer.  
  
 Nesse ponto, você pode usar recursos normais do depurador para iniciar a depuração. Por exemplo, você pode usar **etapa** comandos para continuar a executar seu código linha por linha. Você pode usar o **pilha de chamadas** janela para exibir e controlar o fluxo do script. Você pode usar as janelas variáveis ou **imediato** janela para exibir ou alterar as propriedades e variáveis.  
  
## Mensagens de erro aprimoradas para depuração de scripts  
 Visual Studio fornece mensagens de erro avançadas para problemas de depuração de script comuns. Essas mensagens não aparecem, a menos que você anexe ao Internet Explorer manualmente. Se você encontrar uma condição de erro quando o Internet Explorer é aberto automaticamente, tente anexar manualmente para que você possa ver as mensagens de erro.  
  
## Depuração de aplicativos de Script AJAX  
 Aplicativos de Web habilitados por AJAX usam intensamente o código de script e apresentam desafios especiais de depuração. Para obter informações sobre técnicas de depuração AJAX, consulte  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md).  
  
## Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Limitações na depuração de script](../debugger/limitations-on-script-debugging.md)   
 [Janelas de variável](../Topic/Variable%20Windows.md)   
 [Janela Imediata](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)