---
title: "Solução de problemas de ferramentas de desempenho | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 17612d557b35e41e9d6294c2e449dc637445706b

---
# <a name="troubleshooting-performance-tools-issues"></a>Solução de problemas de ferramentas de desempenho
Você pode ter um dos seguintes problemas ao usar as ferramentas de criação de perfil:  
  
-   [Nenhum dado é coletado pelas ferramentas de criação de perfil](#NoDataCollected)  
  
-   [Números de exibições de relatórios e desempenho para nomes de função](#NoSymbols)  
  
##  <a name="a-namenodatacollecteda-no-data-is-collected-by-the-profiling-tools"></a><a name="NoDataCollected"></a> Nenhum dado é coletado pelas ferramentas de criação de perfil  
 Depois de criar o perfil de um aplicativo, um arquivo de dados (. vsp) de criação de perfil não é criado e você recebe o seguinte aviso na janela de saída ou de comando:  
  
 PRF0025: não foram coletados dados.  
  
 Esse problema pode ser causado por vários motivos:  
  
-   Um processo para o qual foi criado um perfil usando a amostragem ou o método de memória .NET inicia um processo filho que se torna o processo que executa o trabalho do aplicativo. Por exemplo, alguns aplicativos leem a linha de comando para determinar se foram iniciados como um aplicativo do Windows ou um aplicativo de linha de comando. Se um aplicativo do Windows foi solicitado, o processo original iniciará um novo processo configurado como um aplicativo do Windows e o processo original será encerrado. Como as ferramentas de criação de perfil não coletam dados automaticamente para processos filho, nenhum dado é coletado.  
  
     Para coletar dados de criação de perfil nessa situação, anexe o criador de perfil ao processo filho em vez de iniciar o aplicativo com o criador de perfil. Para obter mais informações, consulte [Como anexar e desanexar ferramentas de desempenho para processos em execução](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) e [Attach (VSPerfCmd)](../profiling/attach.md)  
  
##  <a name="a-namenosymbolsa-performance-views-and-reports-display-numbers-for-function-names"></a><a name="NoSymbols"></a> Números de exibições de relatórios e desempenho para nomes de função  
 Depois de criar o perfil de um aplicativo, você verá números em vez de nomes de função em exibições e relatórios.  
  
 Esse problema é causado pela incapacidade do mecanismo de análise de ferramentas de criação de perfil em localizar os arquivos .pdb que contêm as informações de símbolo que mapeiam as informações de código-fonte, nomes de função e números de linha para o arquivo compilado. Por padrão, o compilador cria o arquivo .pdb quando o arquivo de aplicativo é compilado. Uma referência para o diretório local do arquivo .pd é armazenada no aplicativo compilado. O mecanismo de análise busca no diretório referenciado pelo arquivo .pdb e, em seguida, no arquivo que contém atualmente o arquivo do aplicativo. Se o arquivo .pdb não for encontrado, o mecanismo de análise usa os deslocamentos de função em vez de nomes de função.  
  
 Você pode corrigir o problema em uma das duas maneiras:  
  
-   Localize os arquivos .pdb e coloque-os no mesmo diretório dos arquivos de aplicativo.  
  
-   Insira as informações de símbolo no arquivo de dados (. vsp) de criação de perfil. Para obter mais informações, consulte [Salvando informações de símbolo com arquivos de dados de desempenho](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  O mecanismo de análise requer que o arquivo .pdb seja da mesma versão do arquivo de aplicativo compilado. Um arquivo .pdb de um build anterior ou posterior do arquivo do aplicativo não funcionará.


<!--HONumber=Feb17_HO4-->


