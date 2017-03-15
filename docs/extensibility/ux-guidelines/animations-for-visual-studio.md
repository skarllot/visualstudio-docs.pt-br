---
title: "Animações para Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 951e04bc483a68efabee0774467b3e7d4f1fdc28
ms.lasthandoff: 02/22/2017

---
# <a name="animations-for-visual-studio"></a>Animações para Visual Studio
## <a name="animation-fundamentals"></a>Conceitos básicos de animação  
  
### <a name="animation-best-practices-in-visual-studio"></a>Práticas recomendadas de animação no Visual Studio  
 Siga estas regras para garantir a estilos de animação consistentes e amigável em IDE do Visual Studio.  
  
-   **Seja seletivo.** Limitar animações para aqueles que servem para propósitos específicos.  
  
-   **Tempo e velocidade são importantes** para garantir que as transições achar natural e rápida:  
  
    -   Transições animadas concluídas dentro de um meio segundo (500 milissegundos).  
  
    -   Animações que podem ocorrer com frequência precisam ser rápido o suficiente para que eles não interrompam o fluxo de trabalho do usuário.  
  
    -   Animações não devem ser tão rápido ou brusca que é difícil de entender, mas não tão lento que faz um impaciente a transição concluir.  
  
    -   Use tempo variável para enfatizar a importância. Por exemplo, ao navegar por meio de uma sequência de itens em um diagrama de classe, acelerar a transições entre os itens e lenta para se concentrar em itens importantes.  
  
-   **Usar atenuação não linear gradual** de um estado para outro, dando movimento calmo e natural  
  
-   Quando possível, **usar uma animação sutil em foco** para indicar elementos interativos sob o mouse.  
  
-   Se você depende intensamente animações em seus recursos, em seguida, **fornecem um meio para desativá-las** localmente (para todos os seus recursos) como uma opção no **Ferramentas > opções** caixa de diálogo.  
  
-   **Apenas uma animação deve ocorrer em um momento** e transmitir apenas uma informação.  
  
-   **Sutilmente é importante.** Na maioria dos casos animação não precisa de atenção do usuário por demanda para atender sua finalidade. Alterações sutis no prazo, o sequenciamento e comportamento podem afetar significativamente a percepção e podem fazer a diferença entre uma animação eficaz e eficiente.  
  
-   Ao usar animação para chamar atenção para algo, **Certifique-se de que vale a pena interromper o usuário**da linha de pensamento.  
  
-   **Ao mostrar o progresso ou status** através de animação:  
  
    -   Pare mostram o movimento de progresso quando o processo subjacente não está avançando.  
  
    -   Distingui indeterminados processos de processos determinados.  
  
    -   Certifique-se de que uma animação tem identificação estados de conclusão e falha.  
  
    -   Minimize o uso de animações do efeito que mostram o status e certifique-se de que eles têm um valor real, fornecendo informações adicionais de uso real. Os exemplos incluem emergências e alterações de status transitório  
  
#### <a name="do-not"></a>Não:  
  
-   Use movimentos pequeno (movimentação em um pequeno espaço), preferindo desaparece e muda com a movimentação de objetos.  
  
-   Use animações que ocorrem em uma grande área de espaço na tela. Independentemente do tamanho, esse estilo de animação é distração ao usuário.  
  
-   Use animações que não estão relacionados para o objeto que o usuário está atualmente voltado ou interagir com.  
  
-   Use animações que exigem interação do usuário para redefinir o estado, como forçar o usuário a responder a uma notificação piscando para torná-lo parar piscando. Interagir com eles de forma alguma deve ser suficiente para descartá-las.  
  
 Para obter mais informações sobre aplicativos essas práticas recomendadas, consulte [padrões de animação](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).  
  
### <a name="animation-metrics"></a>Métricas de animação  
  
-   O sistema deve reagir visivelmente a gestos do usuário em menos de 10 milissegundos.  
  
-   Transições animadas não devem levar mais de 500 milissegundos para concluir.  
  
-   É uma maneira para compensar as transições que exigem tempos para separá-lo em duas partes; Por exemplo, a primeira parte de uma animação poderia ser o contêiner de conteúdo vazio (até 500 milissegundos) seguido de esmaecimento conteúdo no contêiner (até 500 milissegundos).  
  
-   Para os tempos de carregamento podem ser calculados, um indicador de progresso determinante (indicador de progresso feito por cento) é preferido.  
  
-   Para os tempos de carregamento não podem ser calculados, um indicador de ocupado como um cursor ou uma animação de rotação incorporado (indicador de trabalho ou carregamento) é apropriado.  
  
### <a name="animation-as-communicator"></a>Animação como communicator  
 Na interface do usuário do Visual Studio, a animação funciona apenas como uma ferramenta de comunicação.  Ele é usado para comunicar uma variedade de informações, como alterações estruturais na interface do usuário; Por exemplo, quando um menu abre ou fecha. Animação pode ajudar a visualizar o comportamento dependente de tempo de sistemas complexos, como a visualização do progresso de instalação ou ser usada para atrair a atenção com alertas e notificações.  
  
 Animações de interface do usuário normalmente funcionam de quatro maneiras: visualizar, atrair a atenção, simular e indicar resposta vezes/progresso.  
  
#### <a name="visualize"></a>Visualizar  
 Animação pode enfatizar a natureza tridimensional de objetos e facilitam visualizar sua estrutura espacial. Para fazer isso, a animação pode necessário para girar o objeto em um círculo completo, lentamente ativá-lo e voltar, ou colocar o objeto mais próximo e ligeiramente aumentar seu tamanho para enfatizar a substituição ou o foco.  
  
 Embora objetos tridimensionais podem ser movidos com o controle de usuário, o designer deve determinar antecipadamente (programaticamente ou manualmente) como a melhor animar um movimento que oferece melhor compreensão do objeto. Isso programado animação pode então ser ativado pelo usuário, colocando o cursor sobre o objeto, enquanto os movimentos controlado pelo usuário exigem que o usuário entender como manipular o objeto. Limitar o movimento a um único eixo ou uma orientação ao mesmo tempo; o dimensionar, girar, ou converter, mas não fizer mais de uma simultaneamente.  
  
 A categoria Visualizar inclui os aspectos dos dados, relacionamentos, estado, estrutura, sequência e tempo.  
  
##### <a name="data"></a>Dados  
 Ilustra informações complexas e variável:  
  
-   Movendo por meio de visualizações de informações como gráficos e imagens  
  
-   Percorrendo uma sequência, tour guiado e paginação  
  
-   Chamada de detalhes, apontando e realce informações específicas  
  
-   Sobreposição de detalhes e informações adicionais sobre um elemento focalizado  
  
-   Metamorfose de uma representação estrutural ou organizacional para outro  
  
-   Representando as alterações ao longo do tempo usando os controles deslizantes de tempo, painel giratória rodas e os controles de transporte (play, stop e pause).  
  
##### <a name="relationships"></a>Relações  
  
-   Ilustra como os itens estão relacionados uns aos outros ou quais itens estão relacionados a um determinado item.  
  
-   Mostrar hierarquias e pai-filho ou irmão relações  
  
-   Um elemento gera outra  
  
-   Um elemento minimiza a outro elemento  
  
-   Um elemento vinculado a outro  
  
##### <a name="state"></a>Estado  
  
-   Atualizações de conteúdo.  
  
-   Seleção e o foco do usuário  
  
-   Progresso  
  
-   Erros  
  
##### <a name="structure"></a>Estrutura  
  
-   A estrutura em um nó a dinamização  
  
-   Reorientação  
  
-   Minimizar e maximizar, ou expandir e recolher  
  
##### <a name="sequence"></a>Sequência  
  
-   Sequência de apresentação de slides  
  
-   Folheando imagens  
  
##### <a name="time"></a>Hora  
  
-   Mostrar alterações ao longo do tempo, o tempo decorrido e screencast  
  
-   Mover para o lixo, desfazer e refazer  
  
-   Restaurar o estado do histórico  
  
#### <a name="attract-attention"></a>Atrair a atenção  
 Se o objetivo é chamar a atenção do usuário para um único elemento fora várias ou para alertar o usuário para obter informações atualizadas, uma animação pode ser apropriada. Por exemplo, a página de início de aplicativos pode empregar um botão guia de Introdução que encaixa em vigor depois que a página for carregada.  
  
 Como regra, o último elemento de movimentação na tela atrai a atenção do usuário.  Em uma série de elementos animados, a atenção do usuário será feita após o último objeto de animação.  
  
##### <a name="alert"></a>Alerta  
  
-   Alertar o usuário, atenção, mostre o progresso  
  
-   Mostrar que algo está sendo feito corretamente ou não ou mostrar o progresso ou as alterações de progresso  
  
-   Solicitar aos usuários durante uma tarefa, como localizar mais informações online ou está aprendendo sobre a tarefa atual  
  
##### <a name="notifications"></a>Notificações  
  
-   Alertar o usuário sobre uma condição de erro  
  
-   Interromper o usuário para ver se gostaria de participar de outra coisa  
  
-   Com cuidado, informe ao usuário que um processo foi concluído ou alterados, como quando um download for concluído.  
  
#### <a name="simulate"></a>Simular  
 Esta categoria abrange relacionamento físico tem posto e dimensionalidade.  
  
-   Ilustrar onde objetos vêm ou onde ir para  
  
-   Expandir e recolher ou abrir e fechar  
  
-   Panorâmica, rolagem e página ativa  
  
-   Empilhamento e ordem z  
  
-   Carrossel e Acordeão  
  
-   Invertendo e girando a interface do usuário  
  
#### <a name="response-and-progress-indicators"></a>Indicadores de progresso e de resposta  
 Indicadores de progresso tem algumas vantagens importantes:  
  
-   Ambos os indicadores de progresso determinada e indeterminado reforçar o usuário que o sistema não falhou e está trabalhando no problema.  
  
-   Indicadores de determinada dar ao usuário que uma ideia de quão longe a ação está em andamento, bem como a sensação de receber mais próximo o término.  
  
##  <a name="a-namebkmkanimationpatternsa-animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Padrões de animação  
  
### <a name="overview"></a>Visão Geral  
 Animações no Visual Studio devem atender a uma função específica e não prejudicar a produtividade do usuário. Características de animação gerais a seguir para incluir:  
  
-   Pequena e discreta  
  
-   Naturais e realistas  
  
-   Sutis e subdued  
  
-   Rápido e eficiente  
  
-   Não apressado, reduzida  
  
 A ilustração a seguir mostra os estilos de animação recomendados para uso no Visual Studio. Nenhuma animação e animações sutis desaparecem como / fade out são usados com mais frequência. Aplicativo limitado de movimento animações como expandir e contrair, X e Y para posicionar a alteração e rotação.  
  
 ![Estilos de animação recomendados para o Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "a_VSAnimStyles&1202;")  
  
 **Estilos de animação recomendados para o Visual Studio**  
  
#### <a name="appear-and-disappear"></a>Aparecem e desaparecem  
 Com esse padrão, um elemento alterna entre visível fora do modo de exibição e sem uma animação de transição:  
  
 ![Animação no Visual Studio aparecer/desaparecer](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "b_AppearAndDisappear&1202;")  
  
##### <a name="correct-usage"></a>Uso correto  
 Elementos de interface do usuário atualizados que precisa aparecer ou desaparecer para que o usuário não é distrair nem obstruído instantaneamente. Além disso, animações de movimento lentas podem ser percebidas como arrastar um desempenho, o que não ocorre com o estilo aparecem e desaparecem.  
  
##### <a name="incorrect-usage"></a>Uso incorreto  
 Casos em que interface do usuário aparece abruptamente que o usuário não tem ideia o que aconteceu e adicionar uma animação ajudaria a compreensão contextuais.  
  
##### <a name="animation-properties"></a>Propriedades de animação  
 Geralmente, o tempo de espera é zero segundo.  
  
##### <a name="examples"></a>Exemplos  
  
-   Janelas de ferramentas de ocultar automaticamente  
  
-   Editor de teclado ativado da interface do usuário, como o IntelliSense e a Ajuda do parâmetro  
  
-   Regiões de código de expandir e recolher  
  
#### <a name="fade-in-and-fade-out"></a>Fade in e esmaecimento  
 Com esse padrão, um elemento de interface do usuário faz a transição de não visível (0% de opacidade) visível (100% de opacidade) ou vice-versa:  
  
 ![Fade in/Fade out animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "c_FadeInFadeOut&1202;")  
  
##### <a name="correct-usage"></a>Uso correto  
 Isso é mais recomendado animação da interface do usuário. É um efeito sutil que adiciona interesse sem interromper o fluxo. Em alguns casos, o usuário pode nem mesmo perceber que há uma animação e simplesmente percebe um sistema de interface do usuário fluxo suave.  
  
##### <a name="animation-properties"></a>Propriedades de animação  
  
-   Iniciando a opacidade: 0% de fade in, 100% de esmaecimento  
  
-   Terminando a opacidade: 100% para o fade in, 0% de esmaecimento  
  
-   Duração: 200 milissegundos autônomo, 100 milissegundos quando usado como parte de uma sequência de animação de combinação  
  
-   Estilo de atenuação: InOut seno  
  
##### <a name="examples"></a>Exemplos  
  
-   Janelas de ferramentas de ocultar automaticamente  
  
-   Menu Abrir e fechar  
  
-   Transições de guia de plano de fundo e de primeiro plano  
  
#### <a name="color-blend-from-a-to-b"></a>Mistura de cores de A para B  
 Com esse padrão, um elemento de interface do usuário muda de cor A cor b:  
  
 ![Cor do blend animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "d_ColorBlend&1202;")  
  
##### <a name="correct-usage"></a>Uso correto  
 Como uma transição animada, quando um elemento de interface do usuário altera a cor de um contexto ou estado para outro.  
  
##### <a name="animation-properties"></a>Propriedades de animação  
  
-   A cor inicial: específica da interface do usuário  
  
-   Terminando cor: específica da interface do usuário  
  
-   Duração: 200 milissegundos autônomo, 100 milissegundos quando usado como parte de uma sequência de animação de combinação  
  
-   Estilo de atenuação: InOut seno  
  
##### <a name="examples"></a>Exemplos  
  
-   Transições de estado da janela de documentos (ativo, último ativas e inativas)  
  
-   Transições de estado da janela de ferramenta (focado e foco)  
  
#### <a name="expand-and-contract"></a>Expandir e contrair  
 Com esse padrão, um elemento de interface do usuário se expande em X, Y ou ambas as direções:  
  
 ![Expandir/contrair animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "e_ExpandContract&1202;")  
  
##### <a name="correct-usage"></a>Uso correto  
 Como uma transição animada, quando um elemento de interface do usuário altera o tamanho de um contexto para outro.  
  
##### <a name="animation-properties"></a>Propriedades de animação  
  
-   Escala x: % ou uma dimensão específica (em pixels)  
  
-   Escala Y: % ou uma dimensão específica (em pixels)  
  
-   Posição de ancoragem: geralmente superior esquerdo (para idiomas da esquerda para a direita) ou superior direito (para idiomas da direita para esquerda)  
  
-   Duração: 200 milissegundos autônomo, 100 milissegundos quando usado como parte de uma sequência de animação de combinação  
  
##### <a name="examples"></a>Exemplos  
  
-   Painel do Explorer de arquitetura expandir e recolher  
  
-   Item de página inicial expandir e recolher  
  
#### <a name="x-y-position-change"></a>Alteração de posição X-Y  
 Com esse padrão, um elemento de interface do usuário altera a posição X ou Y ou ambos:  
  
 ![X / Posição Y alterar animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "f_XYPositionChange&1202;")  
  
##### <a name="correct-usage"></a>Uso correto  
 Como uma transição animada, quando um elemento de interface do usuário altera a posição de um contexto para outro.  
  
##### <a name="animation-properties"></a>Propriedades de animação  
  
-   Posição inicial X e Y: específica da interface do usuário  
  
-   Posição final X e Y: específica da interface do usuário  
  
-   Caminho de movimento: nenhum  
  
-   Duração: 200 milissegundos autônomo, 100 milissegundos quando usado como parte de uma sequência de animação de combinação  
  
-   Estilo de atenuação: InOut seno  
  
##### <a name="example"></a>Exemplo  
 Reordenação de guia  
  
#### <a name="rotate"></a>Girar  
 Com esse padrão, gira o elemento de interface do usuário:  
  
 ![Girar animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-g_rotate.png "g_Rotate&1202;")  
  
##### <a name="correct-usage"></a>Uso correto  
 Somente para o indicador de progresso de rotação indeterminado.  
  
##### <a name="animation-properties"></a>Propriedades de animação  
  
-   Grau de rotação: 360  
  
-   Centro de rotação: intermediária do objeto  
  
-   Duração: contínua  
  
##### <a name="example"></a>Exemplo  
 Indicador de progresso indeterminado (rotação)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ações de interface do usuário comuns do shell e animações recomendadas  
  
#### <a name="tab-open"></a>Guia aberta  
  
-   Estilo: aparecem  
  
-   Duração: Zero segundos  
  
 ![Guia animação aberta no Visual Studio](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "h_TabOpen&1202;")  
  
#### <a name="tab-close"></a>Feche o guia  
  
-   Estilo: Alteração de posição X  
  
-   Duração: 200 milissegundos  
  
 ![Guia animação Fechar no Visual Studio](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "i_TabClose&1202;")  
  
#### <a name="tab-reorder"></a>Reordenação de guia  
  
-   Estilo: Alteração de posição X  
  
-   Duração: 200 milissegundos  
  
 ![Guia reordenar animação no Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "j_TabReorder&1202;")  
  
#### <a name="close-floating-document"></a>Fechar documento flutuante  
  
-   Estilo: aparecem  
  
-   Duração: 200 milissegundos  
  
 ![Fechar flutuante animação de documento no Visual Studio](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "k_CloseFloatingDocument&1202;")  
  
#### <a name="window-state-transition"></a>Transição de estado da janela  
  
-   Estilo: Para ser consistente com outras janelas, permitem que o sistema operacional atual definir animação de fechar o documento.  
  
-   Duração: 200 milissegundos  
  
 ![Animação de transição de estado de janela no Visual Studio](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "l_WindowStateTransition&1202;")  
  
#### <a name="menu-open"></a>Menu aberto  
  
-   Estilo: fade in  
  
-   Duração: 200 milissegundos  
  
 ![Animação de menu Abrir no Visual Studio](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "m_MenuOpen&1202;")  
  
#### <a name="menu-close"></a>Fechar menu  
  
-   Estilo: esmaecimento  
  
-   Duração: 200 milissegundos  
  
 ![Animação de menus Fechar no Visual Studio](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "n_MenuClose&1202;")  
  
#### <a name="auto-hide-tool-window-reveal"></a>Revelação de janela de ferramenta ocultar automaticamente  
  
-   Estilo: aparecem  
  
-   Duração: Zero segundos  
  
 ![Ocultar automaticamente animação de janela de ferramenta no Visual Studio](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "o_AutoHideToolWindowReveal&1202;")
