---
title: "Localizar possíveis problemas usando analisadores de mapa de código | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 11
author: alexhomer1
ms.author: ahomer
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ebe6880bdc36dae8b0bf8883c51d9109bba1dbda
ms.lasthandoff: 02/22/2017

---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Encontrar possíveis problemas usando analisadores de mapa de códigos
Executar analisadores em mapas de código para ajudar a identificar o código que pode ser excessivamente complexo ou que precisam de aperfeiçoamento. Por exemplo, você pode usar esses analisadores:  
  
|**Para localizar o código que tem**|**Examine essas áreas para ver se**|  
|-------------------------------|--------------------------------------------|  
|Loops ou dependências circulares|Você pode simplificá-los e considere se é possível dividir esses ciclos.|  
|Muitas dependências|Muitas funções estão realizando ou para determinar o impacto da alteração nessas áreas. Um mapa de código bem formado mostrará um número mínimo de dependências. Para tornar o código mais fácil de manter, alterar, testar e reutilizar, considere se é possível decompor novamente essas áreas para que elas sejam mais claramente definidas, ou se você pode mesclar o código que executa funções semelhantes.|  
|Sem dependências|Eles são necessários ou se você deve remover esse código.|  
  
## <a name="analyze-code-maps"></a>Analisar os mapas de código  
  
1.  Na barra de ferramentas mapa escolha **Layout**, **analisadores**e, em seguida, o analisador que você deseja executar:  
  
    |**Analisador**|**Para identificar nós que**|  
    |------------------|--------------------------------|  
    |**Analisador de referências circulares**|Existem dependências circulares entre eles. **Observação:** dependências circulares no **genéricos** grupo não são mostrados no mapa, ao expandir o grupo.|  
    |**Localizar Hubs Analyzer**|Estão nos principais 25% de nós altamente conectado<br /><br /> **Para ocultar todos os outros nós no mapa**<br /><br /> -Abra o menu de atalho para o mapa, escolha **avançado**, **selecione**, **ocultar não selecionado**.<br />     O mapa oculta os nós não selecionados, e o Analisador identifica novos nós como hubs.|  
    |**Nós não referenciado Analyzer**|Não tem referências de outros nós. **Cuidado:** Verifique se cada um desses casos antes, supondo que o código não é usado. Determinadas dependências como dependências XAML e tempo de execução não podem ser encontradas estaticamente no código.|  
  
 Analisadores de mapa de código continuará a executar após você aplicá-los. Se você alterar o mapa, qualquer analisadores aplicados serão automaticamente reprocessar o mapa atualizado. Para interromper a execução de um analisador, na barra de ferramentas do mapa, escolha **Layout**, **analisadores**. Desative o analisador selecionado.  
  
> [!TIP]
>  Se você tiver um mapa muito grande, executar um analisador pode causar um exceção de memória insuficiente. Se isso ocorrer, edite o mapa para reduzir seu escopo ou gerar uma menor e, em seguida, executar o analisador.  
  
## <a name="see-also"></a>Consulte também  
 [Mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md)   
 [Use mapas de código para depurar seus aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Mapear métodos na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
