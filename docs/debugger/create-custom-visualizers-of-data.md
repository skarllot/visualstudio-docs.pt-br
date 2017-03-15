---
title: "Visualizadores | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.visualizer.troubleshoot"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, visualizadores"
  - "visualizadores"
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os visualizadores são componentes da interface do usuário do depurador do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Um *visualizador* cria uma caixa de diálogo ou outra interface para exibir uma variável ou um objeto de maneira apropriada para o tipo de dados.  Por exemplo, um visualizador de HTML interpreta uma cadeia de caracteres de HTML e exibe o resultado como seria exibido em uma janela do navegador; um visualizador de bitmap interpreta uma estrutura de bitmap e exibe o gráfico que o representa.  Alguns visualizadores permitem modificar assim como exibir os dados.  
  
 O [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] depurador inclui seis visualizadores padrão.  Estes são os visualizadores de texto, HTML, XML, e JSON e todos funcionam em objetos de cadeia de caracteres; o visualizador de árvore do WPF, que exibe as propriedades de uma árvore visual do objeto do WPF; e o visualizador de conjunto de dados, que funciona para objetos de DataSet, DataView e DataTable.  Visualizadores adicionais podem estar disponíveis para download da Microsoft Corporation no futuro e estão disponíveis por meio de terceiros e da comunidade.  Além disso, você pode escrever seus próprios visualizadores e instalá\-los no [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] depurador.  
  
> [!NOTE]
>  Nos aplicativos do **Store**, somente os visualizadores do texto padrão HTML, XML e JSON são suportados.  Não há suporte para visualizadores personalizados \(criados pelo usuário\).  
  
 Os visualizadores são representados no depurador por um ícone de lupa.  Quando você visualiza o ícone de lupa em um **DataTip**, em uma janela de variáveis de depurador ou na caixa de diálogo **QuickWatch**, você pode clicar na lupa para selecionar um visualizador apropriado para o tipo de dados do objeto correspondente.  
  
 Os visualizadores não têm suporte na Compact Framework.  
  
> [!NOTE]
>  Os visualizadores do depurador exigem privilégios maiores do que são permitidos por um aplicativo de confiança parcial.  Como resultado disso, os visualizadores não serão carregados quando você for interrompido no código com confiança parcial.  Para depurar usando um visualizador, você deverá executar o código com confiança total.  
  
## Nesta seção  
 [Como escrever um visualizador](../debugger/how-to-write-a-visualizer.md)  
  
 [Instruções passo a passo: escrevendo um visualizador em C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md)  
  
 [Como testar e depurar um visualizador](../Topic/How%20to:%20Test%20and%20Debug%20a%20Visualizer.md)  
  
 [Referência de API do visualizador](../debugger/visualizer-api-reference.md)  
  
## Seções relacionadas  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)