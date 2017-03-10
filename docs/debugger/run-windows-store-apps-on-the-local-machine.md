---
title: "Executar aplicativos da Windows Store na m&#225;quina local | Microsoft Docs"
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
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Executar aplicativos da Windows Store na m&#225;quina local
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Applies to Windows only](../debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Para depurar, testar ou executar análise de desempenho em um aplicativo da Windows Store, você pode executar o aplicativo no mesmo computador host do Visual Studio.  Se a tela do dispositivo for habilitada para toque, você poderá ativar a funcionalidade completa do aplicativo; do contrário, você estará limitado aos gestos do mouse e do teclado.  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 Você aprende sobre:  
  
 [Como executar em um computador local](#BKMK_How_to_run_on_a_local_machine)  
  
 [Como alternar entre um aplicativo da Windows Store e do Visual Studio em um único monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Como executar em um computador local  
 Para executar o aplicativo no computador local, escolha **Computador Local** na lista suspensa ao lado do botão Iniciar Depuração, na barra de ferramentas **Padrão**.  
  
 ![Executado na máquina Local](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
 Se você não conseguir ver a barra de ferramentas **Padrão**, clique no menu **Exibir**, aponte para **Barra de Ferramentas** e clique em **Padrão**.  
  
 A escolha que você faz na lista suspensa persiste no arquivo de propriedades do projeto e se torna o destino de execução padrão.  
  
 Você também pode definir o destino de execução diretamente no arquivo de propriedades do projeto.  Clique com o botão direito do mouse no nome do projeto no **Gerenciador de Soluções** e escolha **Propriedades**.  Siga um destes procedimentos:  
  
-   Em projetos C\# e Visual Basic, clique em **Depurar** e escolha **Computador Local** da lista suspensa **Dispositivo de Destino**.  
  
     ![Página de propriedades de projeto C&#35; e Visual Basic](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN\_CS\_VB\_ProjProp\_Local")  
  
-   Em projetos C\+\+ e JavaScript, expanda o nó **Propriedades de Configuração**, clique em **Depurar** e escolha **Depurador Local** da lista **Depurador a iniciar**.  
  
     ![Página de propriedades do projeto C&#43;&#43; e JavaScript](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN\_CPP\_JS\_ProjProp\_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Como alternar entre um aplicativo da Windows Store e do Visual Studio em um único monitor  
 **Para alternar de uma instância em execução de um aplicativo da Windows Store ao Visual Studio**  
  
 Quando você executa um aplicativo da Windows Store em um computador local e usa apenas um único monitor, você pode querer alternar para o Visual Studio enquanto deixa o aplicativo em execução.  Por exemplo, o aplicativo pode estar em um estado que não pode ser alcançado por um ponto de interrupção, como esperar por um evento ou estar preso em um loop extenso ou sem fim.  Para retornar ao Visual Studio, pressione ALT\+TAB.