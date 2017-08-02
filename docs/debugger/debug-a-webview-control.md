---
title: "Depurar um controle do WebView | Microsoft Docs"
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
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar um controle do WebView
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows and Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 Para inspecionar e depurar os controles do `WebView` em um aplicativo do Tempo de Execução do Windows, você pode configurar o Visual Studio para anexar o Depurador de Scripts quando iniciar seu aplicativo. No Visual Studio 2013 Update 2, você tem duas formas de interagir com os controles do `WebView` usando o depurador:  
  
-   Abra o [Explorador do DOM](../debugger/quickstart-debug-html-and-css.md) para uma instância do `WebView` e inspecione os elementos de DOM, investigue os problemas de estilo de CSS e teste dinamicamente as mudanças renderizadas nos estilos.  
  
-   Selecione a página da Web ou o `iFrame` exibido na instância `WebView` como alvo na janela [Console do JavaScript](../debugger/javascript-console-commands.md), em seguida, interaja com a página da Web usando os comandos do console. O console dá acesso ao contexto de execução do script atual.  
  
### Anexar o depurador \(C\#, Visual Basic, C\+\+\)  
  
1.  No Visual Studio, adicione um controle `WebView` ao seu aplicativo de Tempo de Execução do Windows.  
  
2.  No Gerenciador de Soluções, abra as propriedades do projeto, escolhendo **Propriedades** do menu de atalho do projeto.  
  
3.  Escolha **Depurar**. Na lista **Processo do aplicativo**, escolha **Script**.  
  
     ![Attach the script debugger](../debugger/media/js_dom_webview_script_debugger.png "JS\_DOM\_WebView\_Script\_Debugger")  
  
4.  \(Opcional\) No caso de versões não Expressas do Visual Studio, desabilite a depuração just\-in\-time \(JIT\) escolhendo **Ferramentas**, **Opções**, **Depuração**, **Just\-In\-Time**,em seguida, desabilite a depuração JIT para o Script.  
  
    > [!NOTE]
    >  Desabilitando a depuração JIT, você pode ocultar caixas de diálogo para exceções não tratadas que ocorrem em algumas páginas da Web. No Visual Studio Express, a depuração JIT sempre fica desabilitada.  
  
5.  Pressione F5 para iniciar a depuração.  
  
### Use o Explorador do DOM para inspecionar e depurar um controle WebView  
  
1.  \(C\#, Visual Basic, C\+\+\) Anexe o depurador do script ao seu aplicativo. Veja a primeira seção para obter instruções.  
  
2.  Se ainda não o fez, adicione um controle `WebView` ao seu aplicativo e pressione F5 para iniciar a depuração.  
  
3.  Navegue até a página que contém os controles `Webview`.  
  
4.  Abra a janela do Explorador do DOM do controle `WebView` escolhendo **Depuração**, **Windows**, **Explorador do DOM** e escolha a URL do `WebView` que deseja inspecionar.  
  
     ![Opening the DOM Explorer](../debugger/media/js_dom_webview.png "JS\_DOM\_WebView")  
  
     O Explorador do DOM associado ao `WebView` aparece como uma nova guia no Visual Studio.  
  
5.  Visualize e modifique elementos de DOM ativos e estilos de CSS, como descrito em [Depurar estilos CSS com o Explorador do DOM](../debugger/debug-css-styles-using-dom-explorer.md).  
  
### Usar a janela Console do JavaScript para inspecionar e depurar um controle WebView  
  
1.  \(C\#, Visual Basic, C\+\+\) Anexe o depurador do script ao seu aplicativo. Veja a primeira seção para obter instruções.  
  
2.  Se ainda não o fez, adicione um controle `WebView` ao seu aplicativo e pressione F5 para iniciar a depuração.  
  
3.  Abra a janela Console do JavaScript para o controle `WebView` escolhendo **Depurar**, **Windows**, **Console do JavaScript**.  
  
     A janela Console do JavaScript aparece.  
  
4.  Navegue até a página que contém os controles `Webview`.  
  
5.  Na janela Console, selecione a página da Web ou um `iFrame` exibido pelo controle `WebView` na lista **Alvo**.  
  
     ![Target selection in the JavaScript console window](~/docs/debugger/media/js_console_target.png "JS\_Console\_Target")  
  
    > [!NOTE]
    >  Usando o console, você pode interagir com um único `WebView`, `iFrame`, compartilhar o contrato ou web worker por vez. Cada elemento requer uma instância separada do host da plataforma web \(WWAHost.exe\). Você pode interagir com um host por vez.  
  
6.  Visualize e modifique variáveis em seu aplicativo ou use comandos do console, como descrito em [Guia de início rápido: Depurar o JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md) e [Comandos do Console JavaScript](../debugger/javascript-console-commands.md).  
  
## Consulte também  
 [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)