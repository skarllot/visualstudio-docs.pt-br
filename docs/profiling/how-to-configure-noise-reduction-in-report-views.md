---
title: "Como configurar redução de ruído em exibições de relatório | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
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
ms.openlocfilehash: 8f0216c8a4b86cf1a7938ce67be8becb71cde400

---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Como configurar redução de ruído em exibições de relatório
Os relatórios de desempenho podem ser configurados para redução de ruído, limitando a quantidade de dados que são apresentados no modo de exibição de Árvore de Chamadas e na exibição de Alocação. Ao usar a redução de ruído, os problemas de desempenho serão mais proeminentes. Isso é útil ao analisar relatórios de desempenho.  
  
 As opções de configuração de redução de ruído incluem as seguintes configurações:  
  
-   **Filtragem** Quando um relatório é analisado, a exibição omitirá funções que se enquadram nas configurações de valor e limite definidos, conforme descrito no procedimento de filtragem a seguir. Por padrão, a filtragem está habilitada.  
  
-   **Dobramento** Se você habilitar o dobramento, as funções consecutivas em um caminho que atenda às configurações que você definiu serão mescladas, conforme descrito no procedimento dobramento a seguir. Por padrão, o dobramento está habilitado.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Para configurar a filtragem para um relatório de desempenho  
  
1.  Quando um modo de exibição de Árvore de Chamadas ou uma exibição de Alocação é mostrada no relatório gerado, no menu **Desenvolvedor**, clique em **Criador de Perfil** e, em seguida, clique em **Opções de Redução de Ruído**.  
  
     A caixa de diálogo **Redução de Ruído** será exibida.  
  
2.  Para habilitar a filtragem, siga estas etapas:  
  
    1.  Selecione **Habilitar Corte**. Essa é a configuração padrão.  
  
        > [!NOTE]
        >  Se a redução de ruído estiver habilitada, uma barra de informações será exibida no relatório. Para obter mais informações, consulte [Modo de exibição de Árvore de Chamadas](../profiling/call-tree-view.md) e [Exibição de Alocações](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configure o valor usando a lista suspensa **Valor** e escolha a configuração aplicável.  
  
    3.  Configure o limite desejado digitando um valor de percentual no caixa de texto **Limite**.  
  
    4.  Para habilitar o aviso de redução de ruído no relatório gerado, selecione **Exibir aviso quando a Redução de Ruído estiver habilitada**. Essa é a configuração padrão.  
  
3.  Para desabilitar a filtragem, desmarque **Habilitar Corte**.  
  
4.  Clique em **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Para configurar o dobramento para um relatório de desempenho  
  
1.  No menu **Desenvolvedor**, clique em **Criador de Perfil** e, em seguida, clique em **Opções de Redução de Ruído**.  
  
     A caixa de diálogo **Redução de Ruído** será exibida.  
  
2.  Para habilitar o dobramento, siga estas etapas:  
  
    1.  Selecione **Habilitar Dobramento**. Essa é a configuração padrão.  
  
        > [!NOTE]
        >  Se a redução de ruído estiver habilitada, uma barra de informações será exibida no relatório. Para obter mais informações, consulte [Modo de exibição de Árvore de Chamadas](../profiling/call-tree-view.md) e [Exibição de Alocações](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configure o valor usando a lista suspensa **Valor** e selecione a configuração aplicável.  
  
    3.  Configure o limite desejado digitando um valor de percentual no caixa de texto **Limite**.  
  
    4.  Para habilitar o aviso de redução de ruído no relatório gerado, selecione **Exibir aviso quando a Redução de Ruído estiver habilitada**. Essa é a configuração padrão.  
  
3.  Para desabilitar o dobramento, desmarque **Habilitar Dobramento**.  
  
4.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando exibições de relatório das ferramentas de desempenho](../profiling/customizing-performance-tools-report-views.md)   
 [Como excluir ou incluir funções curtas por meio da instrumentação](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Modo de exibição de árvore de chamadas](../profiling/call-tree-view.md)   
 [Exibição de alocações](../profiling/dotnet-memory-allocations-view.md)


<!--HONumber=Feb17_HO4-->


