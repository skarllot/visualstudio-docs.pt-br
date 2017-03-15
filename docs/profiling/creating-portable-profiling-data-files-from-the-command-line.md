---
title: "Criação de arquivos de dados de criação de perfil portáteis com a linha de comando | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4affa4c8c89fd66f61ab7c9d407e454b8fa0a9be
ms.lasthandoff: 02/22/2017

---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Criando arquivos de dados de criação de perfil móveis a partir da linha de comando
Para tornar mais fácil o compartilhamento de dados de criação de perfil, você pode usar a ferramenta da linha de comando [VSPerfReport](../profiling/vsperfreport.md) para inserir os símbolos para uma criação de perfil no arquivo .vsp.  
  
 Você também pode criar um arquivo de dados de criação de perfil previamente analisados (.vsps) que é menor e mais rápido para carregar no IDE.  
  
> [!NOTE]
>  Verifique se os arquivos de símbolo (.pdb) estão disponíveis para **VSPerfReport**. Para saber mais, confira [Como especificar locais de arquivos de símbolo na linha de comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Para obter informações sobre o caminho para **VSReport**, confira [Especificação do caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Os dados de criação de perfil em um arquivo .vsps não serão filtrados.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Para inserir os símbolos de uma geração de perfil em um arquivo de dados de criação de perfil (.vsp)  
  
-   Em uma janela de prompt de comando, digite o seguinte comando:  
  
     \<Caminho>**VSPerfReport \<**arquivo VSP> **/PackSymbols**  
  
     Por padrão, o arquivo .vsps é nomeado com o nome base do arquivo .vsp. Você pode especificar um nome alternativo usando a opção **Saída**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Para criar um arquivo de dados de criação de perfil de resumo  
  
-   Em uma janela de prompt de comando, digite o seguinte comando:  
  
     \<Caminho>**VSPerfReport \<**arquivo VSP > **/SummaryFile** [**/Output:**\<nome do arquivo>]  
  
     Por padrão, o arquivo .vsps é nomeado com o nome base do arquivo .vsp. Você pode especificar um nome alternativo usando a opção **Saída**.
