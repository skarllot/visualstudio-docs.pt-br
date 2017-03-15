---
title: "Como usar a janela M&#243;dulos | Microsoft Docs"
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
  - "vs.debug.modules"
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
  - "depurador, Janela Módulos"
  - "depurando [Visual Studio], exibindo módulos"
  - "DLLs, exibindo durante a depuração"
  - "arquivos executáveis, exibindo durante a depuração"
  - "Janela Módulos"
  - "módulos, exibindo"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar a janela M&#243;dulos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Esse recurso não está disponível para depuração do SQL ou script.  
  
 A janela **Módulos** lista as DLLs e EXE que são usados pelo programa e mostra as informações relevantes para cada um.  
  
### Para exibir a janela Módulos no modo de interrupção ou no modo de execução  
  
-   No menu **Depurar**, escolha **Janelas** e clique em **Módulos**.  
  
     Por padrão, a janela **Módulos** classifica os módulos pela ordem de carregamento.  No entanto, você pode escolher classificar por qualquer coluna.  
  
### Para classificar por qualquer coluna  
  
-   Clique no botão na parte superior da coluna.  
  
     Você pode carregar símbolos ou especificar um caminho do símbolo da janela **Módulos** usando o menu de atalho.  
  
## Carregando símbolos  
 Na janela **Módulos**, você pode consultar quais módulos têm símbolos de depuração carregados.  Essas informações são exibidas na coluna **Status do Símbolo**.  Se o status informar **Carregamento ignoradoNão é possível localizar ou abrir o arquivo PDB** ou **Carregamento desabilitado por configuração Incluir\/Excluir**, você poderá dirigir o depurador para baixar símbolos de servidores de símbolos públicos da Microsoft ou carregar símbolos de um diretório de símbolo em seu computador.  Para obter mais informações, consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### Para carregar símbolos manualmente  
  
1.  Na janela **Módulos**, clique com o botão direito do mouse em um módulo para o qual os símbolos não foram carregados.  
  
2.  Aponte para **Carregar Símbolos de** e depois clique em **Servidores de Símbolo Microsoft** ou em **Caminho do Símbolo**.  
  
#### Para alterar as configurações de carregamento do símbolo  
  
1.  Na janela **Módulos**, clique com o botão direito em qualquer módulo.  
  
2.  Clique em **Configurações de Símbolo**.  
  
     Você agora pode alterar as configurações de carregamento do símbolo, conforme descrito em [Especificar o comportamento de carregamento e locais de símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).  As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
#### Para alterar o comportamento de carregamento do símbolo para um módulo específico  
  
1.  Na janela **Módulos**, clique com o botão direito no módulo.  
  
2.  Aponte para **Configurações Automáticas de Carregamento de Símbolos** e clique em **Sempre Carregar Manualmente** ou **Padrão**.  As alterações não terão efeito até você reiniciar a sessão de depuração.  
  
## Consulte também  
 [Breaking Execution](http://msdn.microsoft.com/pt-br/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)