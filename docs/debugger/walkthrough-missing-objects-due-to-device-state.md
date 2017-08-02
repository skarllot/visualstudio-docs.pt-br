---
title: "Instru&#231;&#245;es passo a passo: objetos ausentes devido ao estado do dispositivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: objetos ausentes devido ao estado do dispositivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo demonstra como usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Diagnóstico de gráficos para investigar um objeto que está ausente devido à configurado incorretamente o estado do dispositivo.  
  
 Este passo a passo demonstra como:  
  
-   Use o **lista de eventos gráficos** para localizar possíveis fontes do problema.  
  
-   Use o **estágios de Pipeline gráficos** janela para verificar o efeito do `DrawIndexed` chamadas de API do Direct3D.  
  
-   Use o **histórico de Pixel de gráficos** janela para localizar o problema mais especificamente.  
  
-   Inspecione o estado do dispositivo para possíveis problemas ou configurações incorretas.  
  
## Cenário  
 Um dos motivos que objetos podem não aparecer onde esperados em um aplicativo 3D é um erro de configuração do dispositivo gráfico que faz com que os objetos a serem excluídos da renderização — por exemplo, quando a ordem de contorno causa triângulos a ser removido por engano, ou quando a função de teste de profundidade faz todos os pixels no objeto a ser rejeitadas.  
  
 No cenário descrito neste passo a passo, você apenas atingiu a primeira etapa no desenvolvimento de seu aplicativo 3D e está pronto para testá\-lo pela primeira vez. No entanto, quando você executa o aplicativo, somente a interface do usuário é renderizada na tela. Usando o diagnóstico de gráficos, você capturar o problema em um arquivo de log do gráfico para que você pode depurar o aplicativo. O problema parece com isso no aplicativo:  
  
 ![O aplicativo antes que o problema é corrigido](~/docs/debugger/graphics/media/vsg_walkthru1_firstview.png "vsg\_walkthru1\_firstview")  
  
 Para obter informações sobre como capturar os problemas de gráficos em um log de gráficos, consulte [Capturando informações de gráficos](../debugger/capturing-graphics-information.md).  
  
## Investigação  
 Usando as ferramentas de diagnóstico de gráficos, você pode carregar o arquivo de log de gráficos para inspecionar os quadros que foram capturados durante o teste.  
  
#### Para examinar um quadro em um log de gráficos  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], carregar um log de gráficos que contém um quadro que exibe o modelo ausente. Uma nova guia de diagnóstico de gráficos aparece no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Na parte superior desta guia é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe cada quadro capturado como uma imagem em miniatura.  
  
2.  No **lista quadro**, selecione um quadro que demonstra que o modelo não será exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, os gráficos de log guia é semelhante ao seguinte:  
  
     ![A lista de visualização e quadro de framebuffer do guia .vsglog](~/docs/debugger/graphics/media/vsg_walkthru1_experiment.png "vsg\_walkthru1\_experiment")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode usar o **lista de eventos gráficos** para diagnosticar a ele. O **lista de eventos gráficos** contém todas as chamadas de API da Direct3D que foi feita para processar o quadro ativo, por exemplo, chamadas de API para configurar o estado do dispositivo, para criar e atualizar buffers e desenhar objetos que aparecem no quadro. Muitos tipos de chamadas são interessantes porque há normalmente \(mas nem sempre\) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado, por exemplo desenhar, expedição, copiar ou chamadas claras. Chamadas de desenho são particularmente interessantes porque cada um deles representa a geometria que o aplicativo processado \(chamadas de expedição também podem processar geometria\).  
  
#### Para garantir que estão sendo feitas chamadas de desenho  
  
1.  Abra o **lista de eventos gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **lista de eventos**.  
  
2.  Inspecione o **lista de eventos gráficos** para chamadas de desenho. Para facilitar essa tarefa, digite "Desenhar" no **pesquisa** caixa no canto superior direito do **lista de eventos gráficos** janela. Isso filtra a lista para que ele contém apenas os eventos que têm "Desenhar" em seus cargos. Nesse cenário, você descobre que foram feitas várias chamadas de desenho:  
  
     ![A lista de eventos Graphice mostrando os eventos capturados](~/docs/debugger/graphics/media/vsg_walkthru1_.png "vsg\_walkthru1\_")  
  
 Depois de confirmar que estão sendo feitas chamadas de desenho, você pode determinar qual delas corresponde à geometria ausente. Como você sabe que a geometria ausente não é está sendo desenhada no alvo processado \(neste caso\), você pode usar o **estágios de Pipeline gráficos** janela para determinar qual desenhar o chamada corresponde à geometria ausente. O **estágios de Pipeline gráficos** janela mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito sobre o destino de renderização. Percorrer as chamadas de desenho, os estágios de pipeline são atualizados para mostrar a geometria que está associada essa chamada, e a saída de destino de renderização é atualizada para mostrar o estado do destino de renderização depois que a chamada foi concluída.  
  
#### Para localizar a chamada de desenho de geometria ausente  
  
1.  Abra o **estágios de Pipeline gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **estágios de Pipeline**.  
  
2.  Percorrer cada chamada de desenho enquanto você assiste a **estágios de Pipeline gráficos** janela para o modelo ausente. O **entrada do Assembler** estágio mostra os dados brutos de modelo. O **sombreador de vértices** estágio mostra os dados de modelo transformado. O **sombreador de Pixel** estágio mostra a saída do sombreador de pixel. O **fusão de saída** estágio mostra o destino de renderização mesclada essa chamada de desenho e todas as chamadas de desenho anterior.  
  
3.  Pare quando você atingiu a chamada de desenho que corresponde ao modelo ausente. Nesse cenário, o **estágios de Pipeline gráficos** janela indica que a geometria foi processada, mas não aparecem no destino de renderização:  
  
     ![O Visualizador de pipeline mostra o objeto ausente](~/docs/debugger/graphics/media/vsg_walkthru1_pipeline.png "vsg\_walkthru1\_pipeline")  
  
 Depois de confirmar que o aplicativo processado a geometria ausente e localize a chamada de desenho correspondente, você pode selecionar uma parte da saída de destino de renderização que deve mostrar a geometria ausente e, em seguida, usar o **histórico de Pixel de gráficos** janela para descobrir por que os pixels foram excluídos. O histórico de pixel contém uma lista de todas as chamadas de desenho que podem ter tido um efeito em um determinado pixel. Cada desenho chamar o **histórico de Pixel de gráficos** janela é identificada por um número que também é exibido no **lista de eventos gráficos** janela. Isso ajuda você a confirmar que o pixel deve exibir a geometria ausente e para descobrir por que o pixel foi excluído  
  
#### Para determinar por que o pixel foi excluído  
  
1.  Abra o **histórico de Pixel de gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **histórico de Pixel**.  
  
2.  Com base no **sombreador de Pixel** miniatura, selecione um pixel no framebuffer de saída que deve conter uma parte da geometria ausente. Nesse cenário, a saída do sombreador de pixel deverá abranger a maioria do destino de renderização; Depois que um pixel é selecionado, o **histórico de Pixel de gráficos** janela tem esta aparência:  
  
     ![A janela de histórico de pixel mostra chamadas de desenho relacionados](~/docs/debugger/graphics/media/vsg_walkthru1_hist1.png "vsg\_walkthru1\_hist1")  
  
3.  Confirme se o pixel do destino de renderização selecionado contém uma parte da geometria, correspondendo o número da chamada de desenho que você está analisando \(da **lista de eventos gráficos** janela\) a uma das chamadas de desenho no **histórico de Pixel de gráficos** janela. Se nenhuma das chamadas no **histórico de Pixel de gráficos** correspondência de janela a chamada de desenho que você está analisando, repita essas etapas \(exceto a etapa 1\) até encontrar uma correspondência. Nesse cenário, a chamada de desenho correspondente tem esta aparência:  
  
     ![A janela de histórico de pixel mostrando informações de fragmento](~/docs/debugger/graphics/media/vsg_walkthru1_hist2.png "vsg\_walkthru1\_hist2")  
  
4.  Quando você encontrar uma correspondência, expanda a chamada de desenho correspondente no **histórico de Pixel de gráficos** janela e confirme que o pixel foi excluído. Cada desenho chamar o **histórico de Pixel de gráficos** janela corresponde a um ou mais primitivos geométricos \(pontos, linhas ou triângulos\) que interseção aquele pixel como resultado a geometria do objeto correspondente. Cada interseção de tal pode contribuir para a cor final do pixel. Um primitivo é excluído, pois ele falhou no teste de profundidade é representado por um ícone que mostra a letra Z ao longo de uma seta que se incline para baixo da esquerda para a direita.  
  
5.  Expanda um primitivo excluído para examinar o estado que fez com que ele seja excluído. No **Output Merger** grupo, mova o ponteiro sobre o **resultado**. Uma dica de ferramenta indica por que o primitivo foi excluído. Nesse cenário, a análise revela que o primitivo foi excluído porque ele não passou no teste de profundidade e, portanto, não contribui com a cor final do pixel.  
  
 Depois de determinar que a geometria não aparece porque seus primitivos de falha no teste de profundidade, você pode suspeitar que esse problema está relacionado ao estado do dispositivo configurado incorretamente. Estado do dispositivo e outros Direct3D objeto dados podem ser examinados usando o **tabela de objetos gráficos**.  
  
#### Para examinar o estado do dispositivo  
  
1.  Abra o **tabela de objetos gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **objeto tabela**.  
  
2.  Localize o **dispositivo D3D10** objeto o **tabela de objetos gráficos**, e, em seguida, abra o **dispositivo D3D10** objeto. Um novo **dispositivo d3d10** guia é aberta no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para facilitar essa tarefa, você pode classificar o **tabela de objetos gráficos** por **tipo**:  
  
     ![A tabela de objetos gráficos e o estado do dispositivo relacionado](~/docs/debugger/graphics/media/vsg_walkthru1_objtable.png "vsg\_walkthru1\_objtable")  
  
3.  Examine o estado do dispositivo é exibido no **dispositivo d3d10** guia problemas em potencial. Porque a geometria não aparece porque seus primitivos de falha no teste de profundidade, você pode se concentrar no estado do dispositivo, como o estêncil de profundidade, o que afeta o teste de profundidade. Nesse cenário, o **Descrição de estêncil profundidade** \(em **estado fusão de saída**\) contém um valor comum para o **função profundidade** membro, `D3D10_COMPARISON_GREATER`:  
  
     ![A janela do dispositivo de D3D10 mostrando informações de estêncil de profundidade](~/docs/debugger/graphics/media/vsg_walkthru1_devicestate.png "vsg\_walkthru1\_devicestate")  
  
 Depois de determinar que a causa do problema de renderização pode ser uma função de profundidade configurado incorretamente, você pode usar essas informações junto com seu conhecimento sobre o código para localizar onde a função de profundidade foi definida incorretamente e corrigir o problema. Se você estiver familiarizado com o código, você pode procurar o problema usando pistas reunidas enquanto você o estava depurando — por exemplo, com base no **Descrição de estêncil profundidade** nesse cenário, você pode pesquisar o código para palavras como "profundidade" ou "GREATER". Depois de corrigir o código, recompilá\-lo e executar o aplicativo novamente para descobrir o que é resolvido o problema de renderização:  
  
 ![O aplicativo depois que o problema for corrigido](~/docs/debugger/graphics/media/vsg_walkthru1_finalview.png "vsg\_walkthru1\_finalview")