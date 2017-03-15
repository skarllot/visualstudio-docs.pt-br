---
title: "Passo a passo: capturando informa&#231;&#245;es de gr&#225;ficos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Passo a passo: capturando informa&#231;&#245;es de gr&#225;ficos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo demonstra como usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Diagnóstico de gráficos manualmente capturar informações gráficas de um aplicativo Direct3D.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Interceptação de diagnóstico de gráficos para seu aplicativo  
  
-   Capturando informações de gráficos  
  
## Capturando informações de gráficos  
 Para usar as ferramentas de diagnóstico de gráficos, primeiro você precisa capturar as informações de gráficos que ele depende. Para habilitar a captura, use o **Iniciar diagnóstico** comando vincular o diagnóstico de gráficos para seu aplicativo quando ele for iniciado.  
  
#### Para habilitar a captura de informações de gráficos depois de uma solução ou projeto é carregado  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], carregar um arquivo de projeto ou solução para o aplicativo que você deseja capturar informações de gráficos.  
  
2.  Na barra de ferramentas de diagnóstico de gráficos, escolha **Iniciar diagnóstico**.  
  
#### Para habilitar a captura de informações de gráficos sem carregar uma solução ou projeto  
  
1.  Na barra de menus, escolha **arquivo**, **Abrir**, **projeto\/solução**. O **Abrir projeto** caixa de diálogo é exibida.  
  
2.  Em vez de um arquivo de projeto ou solução, especifique o arquivo executável do aplicativo que você deseja capturar informações de gráficos e, em seguida, escolha **Abrir**.  
  
3.  Na barra de menus, escolha **Depurar**, **gráficos**, **Iniciar diagnóstico**.  
  
 Após iniciar o aplicativo e quadros de renderização, você pode capturar informações gráficas.  
  
#### Para capturar informações gráficas  
  
-   Na barra de ferramentas de diagnóstico de gráficos, escolha o **capturar** botão.![Ícone de botão de captura de gráficos](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     \- ou \-  
  
     Com o aplicativo no foco, pressione **Print Screen**.  
  
 Cada vez que você capturar informações sobre um quadro, diagnóstico de gráficos registra os eventos do Direct3D e o estado associado e adiciona esses dados em um log de gráficos. Um novo log de gráficos é criado para cada sessão de diagnóstico de gráficos. Para obter informações sobre logs de gráficos, consulte [Visão Geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Próximas etapas  
 Este passo a passo demonstrou como capturar informações gráficas manualmente. Como uma próxima etapa, considere esta opção:  
  
-   Aprenda a analisar informações gráficas capturadas usando as ferramentas de diagnóstico de gráficos. Consulte [Visão Geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Consulte também  
 [Capturando informações de gráficos](../debugger/capturing-graphics-information.md)