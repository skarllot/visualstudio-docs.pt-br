---
title: "Criando arquivos de dados de cria&#231;&#227;o de perfil m&#243;veis a partir da linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Criando arquivos de dados de cria&#231;&#227;o de perfil m&#243;veis a partir da linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para facilitar o compartilhamento de dados do perfil, você pode usar a ferramenta de linha de comando [VSPerfReport](../profiling/vsperfreport.md) para inserir os símbolos para analisar executado no arquivo de .vsp.  
  
 Você também pode criar um arquivo de analisar os dados de criação de perfil .vsps \(\) que é menor e é mais rápido carregar no IDE.  
  
> [!NOTE]
>  Verifique se os arquivos do símbolo \(.pdb\) estão disponíveis para **VSPerfReport**.  Para obter mais informações, consulte [Como especificar locais de arquivo de símbolo a partir da linha de comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Para obter informações sobre o caminho para **VSReport**, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Os dados de criação de perfil em um arquivo de .vsps não podem ser filtrados.  
  
### Para inserir os símbolos para analisar executado em dados de perfil .vsp arquivo \(\)  
  
-   Em uma janela de prompt de comando, digite o seguinte comando:  
  
     \<Caminho\>**VSPerfReport \<**VSP Arquivo\> **\/PackSymbols**  
  
     Por padrão, o arquivo de .vsps é nomeada com o nome de arquivo de .vsp.  Você pode especificar um nome alternativo usando a opção de **Output** .  
  
### Para criar um arquivo de resumo dos dados de criação de perfil  
  
-   Em uma janela de prompt de comando, digite o seguinte comando:  
  
     \<Caminho\>**VSPerfReport \<**VSP Arquivo\> **\/SummaryFile** \[nome do\<arquivo de\>**\/Output:**\]  
  
     Por padrão, o arquivo de .vsps é nomeada com o nome de arquivo de .vsp.  Você pode especificar um nome alternativo usando a opção de **Output** .