---
title: VSPerfMon | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
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
ms.openlocfilehash: 3844a07a1ccf989baf37326c4af183dc32bc1451

---
# <a name="vsperfmon"></a>VSPerfMon
Você pode usar a ferramenta VSPerfMon para coletar dados de desempenho para um aplicativo. Normalmente essa ferramenta é iniciada pelo VSPerfCmd.exe. VSPerfMon exibe informações adicionais sobre como anexar ou desanexar processo que não está disponível usando a ferramenta VSPerfCmd. Para exibir essas informações, inicie o VSPerfMon em uma janela separada. Para invocar VSPerfMon use a seguinte sintaxe:  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 A tabela a seguir descreve as opções da ferramenta VSPerfMon:  
  
|Opções|Descrição|  
|-------------|-----------------|  
|**U**|Saída de console redirecionada gravada como Unicode.  Deve ser a primeira opção especificada.|  
|**OUTPUT:** `<` *nome do arquivo* `>`|Redireciona a saída para o nome de arquivo especificado.|  
|**TRACE**|Inicia o monitor de desempenho para criação de perfil instrumentada.|  
|**SAMPLE**|Inicia o monitor de desempenho para criação de perfil de amostragem.|  
|**COVERAGE**|Inicia o monitor de desempenho para coleta de dados de cobertura de código.|  
|**CONCURRENCY**|Inicia o monitor de desempenho para criação de perfil de contenção de recursos.|  
|**USER:** `[` *domínio* `\]` *nome do usuário*|Permite o acesso do cliente ao monitor de desempenho da conta especificada.|  
|**CROSSSESSION**|Habilitar criação de perfil de sessão cruzada.|  
|**COUNTER** `:cfg`|Quando o método de criação de perfil (TRACE) de instrumentação é usado, especifica um contador de CPU a ser coletado em cada ponto de instrumentação. Você pode coletar dados do contador de vários especificando diversas opções de contador.<br /><br /> Use a sintaxe a seguir para especificar os dados do contador (*cfg*):<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** é o nome de um contador retornado pelo comando VSPerfCmd /QueryCounters.<br />-   **Reload** é o intervalo de amostragem de eventos do contador. Não use *Reload* com o método de instrumentação.<br />– Quando especificado, **FriendlyName** substitui **CounterName** em nomes de coluna de relatório em ferramentas de criação de perfil.|  
|**WINCOUNTER** `:path`|Especifica um contador de desempenho do Windows para incluir com os dados de marca. `path` é uma cadeia de caracteres do contador de desempenho do Windows no formato de caminho de contador PDH. Por exemplo:<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|  
|**AUTOMARK** `:n`|Especifica o intervalo de tempo (em milissegundos) entre as marcas automática quando você usa /WINCOUNTER. Arredondado para cima até a 500 ms mais próximos.<br /><br /> Use 0 para desabilitar marcas automáticas. (padrão=500 ms se não especificado)|  
  
## <a name="see-also"></a>Consulte também  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Exibições de relatório de desempenho](../profiling/performance-report-views.md)


<!--HONumber=Feb17_HO4-->


