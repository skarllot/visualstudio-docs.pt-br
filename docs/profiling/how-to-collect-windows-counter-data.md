---
title: Como coletar dados do contador do Windows | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
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
ms.openlocfilehash: 4767e3ed9481dad3b4d22a01eed89a2835d43213

---
# <a name="how-to-collect-windows-counter-data"></a>Como coletar dados do contador do Windows
Os contadores do Windows são contadores de desempenho do sistema que podem ser coletados em intervalos definidos durante a criação de perfil. Na exibição de Marcas do relatório das Ferramentas de Criação de Perfil, uma linha é rotulada **AutoMark** para cada intervalo de coleta. A linha contém colunas que descrevem os valores do contador de desempenho nesse intervalo. Para restringir a análise para um período de tempo entre duas marcas específicas, selecione as marcas, clique com o botão direito do mouse e, em seguida, selecione **Filtrar por** ->  **Marcas** no menu de atalho.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos da Windows Store também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Para coletar dados do contador do Windows  
  
1.  No Gerenciador de Desempenho, clique com botão direito do mouse na sessão para a qual você deseja configurar os contadores do Windows e selecione **Propriedades**.  
  
2.  Nas **Páginas de Propriedades**, clique em **Contadores do Windows**.  
  
3.  Selecione a caixa de seleção **Coletar Contadores do Windows**.  
  
4.  Na caixa de texto **Intervalo de coleta (ms)**, digite um intervalo de tempo.  
  
5.  Selecione uma categoria da lista suspensa **Categoria de Contador**.  
  
6.  Selecione uma instância da lista suspensa de **Instância**.  
  
7.  Selecione os contadores que você deseja usar ao analisar seu aplicativo.  
  
8.  Clique em **Aplicar.**  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)   
 [Contadores da CPU e do Windows](../profiling/cpu-and-windows-counters.md)


<!--HONumber=Feb17_HO4-->


