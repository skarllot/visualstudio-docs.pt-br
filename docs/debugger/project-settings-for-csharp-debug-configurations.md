---
title: "Defini&#231;&#245;es do projeto para configura&#231;&#245;es de depura&#231;&#227;o do C# | Microsoft Docs"
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
  - "depurar compilações, configurações de projeto"
  - "depurar configurações, C#"
  - "depurar configurações, J#"
  - "depurando [C#], depurando configurações"
  - "depurando [J#], depurando configurações"
  - "configurações do projeto, depurar"
  - "configurações do projeto [Visual Studio], depurar configurações"
  - "projetos [Visual Studio], depurar configurações"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Defini&#231;&#245;es do projeto para configura&#231;&#245;es de depura&#231;&#227;o do C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode alterar as configurações do projeto para uma configuração de depuração C\# na janela **Páginas de Propriedades**, conforme discutido em [Configurações de depuração e lançamento](../debugger/how-to-set-debug-and-release-configurations.md).  As tabelas a seguir mostram onde localizar configurações relacionadas ao depurador na janela **Páginas de Propriedades**.  
  
> [!WARNING]
>  Este tópico não se aplica a aplicativos da Windows Store.  Consulte [Iniciar uma sessão de depuração \(VB, C\#, C\+\+ e XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Guia Depurar  
  
|**Configuração**|**Descrição**|  
|----------------------|-------------------|  
|**Configuração**|Define o modo para compilar o aplicativo.  Escolha entre **Ativa \(depuração\)**, **Depurar**, **Versão**, **Todas as Configurações**.|  
|**Iniciar Ação**|Este grupo de controles Especifica a ação que ocorrerá quando você escolhe Start a partir do menu Debug.<br /><br /> -   **Iniciar projeto** é o padrão e inicia o projeto de inicialização para depuração.  Para obter mais informações, consulte [Escolhendo o projeto de inicialização](http://msdn.microsoft.com/pt-br/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Iniciar programa externo** permite iniciar e anexar a um programa que não faz parte de um projeto do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obter mais informações, consulte [Anexando a um programa em execução](http://msdn.microsoft.com/pt-br/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Iniciar navegador na URL** permite depurar um aplicativo Web.|  
|**Argumentos de linha de comando**|Especifica argumentos de linha de comando para o programa ser depurado.  O nome do comando é o nome do programa especificado em Iniciar programa externo.  Se Iniciar Ação for definida para iniciar URL, os argumentos de linha de comando não podem ser especificados.|  
|**Diretório de trabalho**|Especifica o diretório de trabalho do programa que está sendo depurado.  No [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], o diretório de trabalho é o diretório a partir do qual o aplicativo é iniciado de \\bin\\debug por padrão.|  
|**Use o computador remoto**|No nome de um computador remoto no qual o aplicativo executará para fins de depuração ou um [Nome do servidor Msvsmon](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  O local do EXE no computador remoto é especificado pela propriedade Caminho da Saída na pasta Propriedades de Configuração, categoria Compilação.  O local deve ser um diretório compartilhável no computador remoto.|  
|**Habilitar depuração de código não gerenciado**|Permite depurar chamadas para código nativo do Win32 \(não gerenciado\) de seu aplicativo gerenciado.|  
|**Habilitar a depuração do SQL Server**|Permite depuração de objetos de banco de dados do SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Guia Compilação  
  
|Configuração|Descrição|  
|------------------|---------------|  
|**Símbolos de compilação condicional:**|As constantes DEBUG e TRACE são definidas aqui.<br /><br /> Essas constantes habilitam a compilação condicional da [Classe Debug](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) e da [Classe Trace](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx).  Com essas constantes definidas, os métodos da classe Debug e Trace geram saída para a [Janela de Saída](../ide/reference/output-window.md).  Sem essas constantes, os métodos da classe Debug e Trace não são compilados e nenhuma saída será gerada.<br /><br /> -   A depuração é definida normalmente na versão de depuração de um programa e indefinida na versão de lançamento.<br />-   O rastreamento geralmente é definido nas versões de Depuração e Versão.|  
|**Código de otimização**|A menos que você encontre um bug que apareça somente no código otimizado, deverá deixar essa configuração desativada na versão de Depuração.  O código otimizado é mais difícil de depurar porque as instruções não correspondem diretamente a instruções em suas janelas de origem.|  
|**Caminho de saída:**|Normalmente definido para bin\\Debug para depuração.|  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)