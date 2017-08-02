---
title: "Padrões compostos para o Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
caps.latest.revision: 8
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
ms.openlocfilehash: a0b2c44cca934a0b6e338ee5ae72eba1489521d7
ms.lasthandoff: 02/22/2017

---
# <a name="composite-patterns-for-visual-studio"></a>Padrões compostos para o Visual Studio
Padrões compostos combinam elementos de design e interação em configurações distintas. Alguns dos mais importantes compostos padrões no Visual Studio com relação a consistência incluem:  
  
-   [Visualização de dados](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)  
  
-   [Interface do usuário no objeto e inspecionar](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
-   [Modelos de seleção](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
-   [Persistência e salvar as configurações](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
-   [Entrada por toque](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)  
  
##  <a name="a-namebkmkdatavisualizationa-data-visualization"></a><a name="BKMK_DataVisualization"></a>Visualização de dados  
  
### <a name="overview"></a>Visão Geral  
 Os gráficos são uma maneira visual de agregar e visualizar dados a fim de melhorar a tomada de decisões. Eles podem ajudar os usuários enfrentados muitos dados, mas pouco significando ver o que merece atenção e que pode ser uma ação.  
  
 O usuário se beneficiará de um gráfico se qualquer uma das seguintes condições forem verdadeiras:  
  
-   O gráfico ajudará os usuários a identificar as tarefas que possam agir em?  
  
-   O gráfico permitirá que os usuários prever as consequências de possíveis alterações?  
  
-   O gráfico ajudará os usuários a descobrir tendências e identificar padrões?  
  
-   O gráfico permitirá que os usuários a tomar decisões melhores?  
  
-   O gráfico ajudará a responder a perguntas específicas que os usuários podem ter no contexto especificado?  
  
#### <a name="general-rules-for-charts"></a>Regras gerais para gráficos  
  
-   Rotular dados claramente. Ilustrações sem explicação são apenas belas fotos.  
  
-   Inicie eixos em zero para evitar distorcer proporções. Tamanho da linha de comprimento e barra são indicações visuais importantes para entender as relações entre os pontos de dados.  
  
-   Crie gráficos, não infográficos. Infográficos são artísticas representações de dados, e sua meta principal é storytelling visual. Gráficos podem (e devem) ser visualmente atraente, mas permitir que os dados falem por si.  
  
-   Evite skeumorphism, ilustrados gráficos de barras, contraste hashmarks e outros infográfico toques.  
  
-   Não use efeitos 3D como um elemento decorativo. Use-os somente se eles realmente integral para a capacidade do usuário para compreender as informações.  
  
-   Evite usar várias linhas e preenchimentos, como mais de duas cores podem fazer esse tipo de gráfico difíceis de ler e interpretar corretamente.  
  
-   Não use um gráfico (ou qualquer ilustração) como o único meio de compreensão de um conceito ou interagir com dados. Isso apresenta problemas para usuários com deficiências visuais.  
  
-   Não use gráficos como gratuitas ou decorativos elementos em uma página. Em outras palavras, se um gráfico não adiciona que qualquer valor ou ajuda usuários a resolver um problema, não usá-lo.  
  
### <a name="chart-types"></a>Tipos de gráfico  
 Tipos de gráficos usados no Visual Studio incluem gráficos de barras, gráficos de linha, um gráfico de pizza modificado, conhecido como um gráfico de anel ou "gráfico de rosca", cronogramas, dispersão plotagens (também chamadas de "gráficos de cluster") e os gráficos de Gantt. Cada tipo de gráfico é útil para comunicar-se um tipo diferente de informação.  
  
### <a name="other-charting-considerations"></a>Outras considerações sobre a criação de gráficos  
  
#### <a name="color"></a>Cor  
 Há uma paleta específica de gráficos cores definidas para uso no Visual Studio. A paleta é acessível para os principais tipos de cegueira e as cores podem ser diferenciadas mesmo quando usado como muito estreitas fatias da cor. Você pode usar essas cores em qualquer combinação para qualquer tipo de gráfico em sua interface do usuário. Você não precisa usar todas as sete cores se você não precisar que muitas cores distintas. Essas cores não foram projetadas para ser usado com qualquer elemento de primeiro plano, para não colocar texto ou glifos sobre essas cores. Esses matizes devem ser codificadas e expostos a personalização do usuário em **Ferramentas > opções** (consulte [expondo cores para os usuários finais](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)).  
  
|Amostra de|Hex|RGB|  
|------------|---------|---------|  
|![Amostra 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|  
|![Amostra BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|  
|![Amostra FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|  
|![Amostra 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|  
|![Amostra 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|  
|![Amostra 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|  
|![Amostra B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|  
  
##  <a name="a-namebkmkonobjectuia-on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>Interface do usuário no objeto e inspecionar  
 Esta seção fornece o contexto para inspeção, também conhecida como exibição de inspeção de código, um tipo de objeto de interface de usuário exclusivo para o Visual Studio.  
  
### <a name="overview"></a>Visão Geral  
  
-   Interface do usuário no objeto deve fornecer ao usuário mais informações ou interatividade sem desviar a atenção de sua tarefa principal.  
  
-   O padrão principal para o objeto da interface do usuário no Visual Studio é conhecido como "informações no ponto de atenção".  
  
-   Interface do usuário no objeto no Visual Studio é embutido ou flutuante e seja durável ou transitório.  
  
    -   Exibição de inspeção de código, um tipo de objeto da interface do usuário no Visual Studio, é embutida e durável.  
  
    -   CodeLens, um tipo de objeto da interface do usuário no Visual Studio, é transitório e flutuantes  
  
 Compreendendo como funciona um trecho de código, ou localizar detalhes sobre esse código, geralmente requer um desenvolvedor alternar o contexto e vá para outros tipos de conteúdo ou de outra janela. Essas mudanças de contexto podem ser prejudicial, porque os usuários podem perder o foco na sua tarefa original se ele deixar a janela principal. Além disso, obtendo que original de volta de contexto pode ser difícil, especialmente se alternar janelas causou seu código original para ser obscurecida por outra interface de usuário.  
  
 Interface do usuário no objeto segue um padrão chamado "informações no ponto de atenção". Essas mensagens, janelas pop-up e caixas de diálogo dar aos usuários informações adicionais relevantes que adiciona esclarecimento ou interatividade sem perder o foco na sua tarefa principal. Interface do usuário no objeto exemplos de janelas pop-up que aparecem quando um usuário passar o ponteiro do mouse sobre um ícone na área de notificação, a pequena curva vermelha sob uma palavra incorreta e o modo de exibição de espiada introduzido no Visual Studio 2013.  
  
### <a name="decision-points"></a>Pontos de decisão  
 No Visual Studio, há várias maneiras de usar esse padrão de informações no ponto de atenção. Escolhendo o mecanismo certo e implementá-lo de maneira consistente e previsível são essencial para a experiência geral. Caso contrário, podem ser apresentado aos usuários uma experiência confusa ou inconsistente que prejudica o foco do próprio conteúdo.  
  
#### <a name="relationships-between-master-and-detail-content"></a>Relações entre mestre e de detalhes de conteúdo  
 Informações no ponto de atenção são usadas para exibir uma relação entre o conteúdo que o usuário está focalizado (o conteúdo "mestre") e adicionais relacionados ao conteúdo (o "Detalhes"). Nesse padrão, o conteúdo de detalhes é claramente relacionado ao conteúdo, o usuário está trabalhando com e pode ser exibido próximo o conteúdo mestre. Informações complementares ou informações que não podem ser resumidas sem sobrecarregar o conteúdo mestre devem seguir outro padrão, como uma janela de ferramenta.  
  
-   **Sempre** exibir o conteúdo de detalhes em proximidade com o conteúdo mestre.  
  
-   **Sempre** Certifique-se de que o conteúdo de detalhes ainda permite que o usuário permaneça voltado para o conteúdo principal. Muitas vezes, a melhor maneira de conseguir isso é renderizar o conteúdo de detalhes como perto o conteúdo mestre possível. Isso pode ser feito por processar o conteúdo de detalhes em uma janela pop-up ao lado do conteúdo mestre ou tornando o conteúdo de detalhes internamente sob o conteúdo mestre.  
  
-   **Nunca** use informações no ponto de atenção que leva o usuário para fora o conteúdo mestre. Se os usuários precisam visualizar o conteúdo de detalhes separadamente, expor uma ação explícita que permite ao usuário fazer isso.  
  
#### <a name="design-details"></a>Detalhes do projeto  
 Depois de ter determinado que a interface do usuário no objeto é a escolha certa, há quatro considerações de design principais:  
  
1.  **Persistência:** o conteúdo deve ser durável ou transitório?   
    Os usuários desejam manter as informações visíveis para consultar ou interagir com? Ou, os usuários desejarão visão rapidamente as informações e continue com a sua tarefa principal?  
  
2.  **Tipo de conteúdo:** o conteúdo será informativa, acionáveis ou navegação?   
    O usuário precisa detalhes adicionais sobre o conteúdo mestre? O usuário precisa concluir uma tarefa que afeta o conteúdo mestre? Ou o usuário precisa ser direcionada para outro recurso?  
  
3.  **Tipo de indicador:** um indicador de ambiente faz sentido?   
    As informações podem ser resumidas em uma maneira útil e exibidas sem sobrecarregar o conteúdo mestre?  
  
4.  **Gestos:** quais gestos serão usado para invocar e ignorar a interface do usuário?   
    Como o usuário exibir o conteúdo de detalhes e enviá-lo imediatamente? Há um valor ao adicionar um gesto como fixação para alternar entre os estados transitórios e duráveis?  
  
 Cada um desses pontos de quatro decisão terá impacto sobre os principais componentes da interface do usuário no objeto.  
  
### <a name="on-object-ui-components"></a>Componentes de interface do usuário no objeto  
  
1.  Tipo de contêiner (apresentador de conteúdo)  
  
    -   Flutuante  
  
    -   Embutido  
  
2.  Tipo de conteúdo  
  
    -   Informação: dados que podem ser estáticos ou dinâmicos  
  
    -   Acionáveis: comandos que alteram o conteúdo mestre  
  
    -   Navegação: links que levam o usuário para outra janela ou aplicativo, como o MSDN  
  
3.  Gestos  
  
    -   Invocação  
  
    -   Demissão  
  
    -   Fixando  
  
    -   Outras interações  
  
4.  Modelo de persistência e confirmação  
  
    -   Transitório  
  
    -   Duráveis  
  
    -   Automático  
  
    -   Sob demanda  
  
5.  Indicadores de ambiente (opcionais)  
  
    -   Sublinhado Rabisco  
  
    -   Ícone de marca inteligente  
  
    -   Outros indicadores de ambiente  
  
#### <a name="container-content-presenter-type"></a>Tipo de contêiner (apresentador de conteúdo)  
 Há duas opções principais para apresentar conteúdo no ponto de atenção:  
  
1.  **Embutido:** um apresentador embutidos, como o modo de exibição de espiada que foi introduzido no Editor do Visual Studio 2013 código, torna o espaço para o novo conteúdo, alternando o conteúdo existente.  
  
    -   **Prefira** embutido apresentadores se você espera que os usuários desejam gastar uma quantidade significativa de tempo se referir ao ou interagir com o conteúdo presente.  
  
    -   **Evite** embutido apresentadores se você espera que os usuários desejarão Observe as informações presentes, e continuar sua tarefa principal com um mínimo de interrupção.  
  
2.  **Flutuante:** um apresentador flutuante é posicionado mais próximo ao conteúdo selecionado possível, mas não altera o layout do conteúdo existente. Várias estratégias podem ser empregadas, como exibir um painel flutuante de conteúdo sobre o mais próximo disponível espaço em branco do símbolo selecionado.  
  
    -   **Prefira** flutuante apresentadores se você espera que os usuários desejarão Observe as informações presentes, e continuar sua tarefa principal com um mínimo de interrupção.  
  
    -   **Evite** flutuante apresentadores se você espera que os usuários desejarão gastam uma quantidade significativa de tempo se referir ao ou interagir com o conteúdo de apresentação.  
  
#### <a name="content-type"></a>Tipo de conteúdo  
 Há três tipos principais de conteúdo que pode ser exibido dentro de qualquer contêiner de interface do usuário no objeto. Qualquer combinação desses tipos de informações pode ser mostrada. Os três tipos são:  
  
1.  **Informação:** mais contêineres de interface do usuário exibirá algum tipo de conteúdo informativo ao objeto. O conteúdo pode representar informações sobre o estado atual do ambiente ou pode representar informações sobre estado potencial futura do ambiente. Por exemplo, ele pode ser usado para mostrar o efeito de um comando específico, como uma refatoração, no código existente.  
  
    -   **Sempre** usar a representação canônica das informações que você exibir. Por exemplo, o código deve se parecer com o código, completo com realce de sintaxe e deve respeitar a fonte e outras configurações de ambiente que o usuário tiver definido.  
  
    -   **Sempre** considerar as ações de suporte sobre o conteúdo de informação que seria possível se essas mesmas informações são apresentadas como conteúdo mestre. Por exemplo, se apresentar o código existente dentro de um contêiner de interface do usuário no objeto, considere seriamente a capacidade de procurar e modificar o código de suporte.  
  
    -   **Sempre** considere usar uma cor de plano de fundo diferente se apresentar conteúdo informativo que representa um estado futuro potencial.  
  
2.  Acionáveis: alguns contêineres de interface do usuário no objeto fornece a capacidade de realizar alguma ação sobre o conteúdo mestre, como a execução de uma operação de refatoração.  
  
    -   **Sempre** posicionar acionáveis comandos separadamente do conteúdo informativo.  
  
    -   **Sempre** habilitar e desabilitar ações quando apropriado.  
  
    -   **Sempre** consulte as diretrizes padrão para representar os comandos nas caixas de diálogo.  
  
    -   **Sempre** manter o número de ações que são expostos em um contêiner de interface do usuário no objeto seja mínimo. Interagir com a interface do usuário no objeto deve ser uma experiência simples e rápida. O usuário não deve fazer no próprio contêiner de interface do usuário no objeto de gerenciamento de energia.  
  
    -   **Sempre** considerar como e quando um contêiner de interface do usuário do objeto será fechado ou descartado. Como prática recomendada, qualquer ação que conclui a caixa de diálogo entre o mestre e de detalhes de conteúdo também deve fechar o contêiner de interface do usuário no objeto quando essa ação é invocada.  
  
3.  **Navegação:** alguns no objeto da interface do usuário contêineres incluem links que levam o usuário para outra janela ou aplicativo, como a abertura de um artigo do MSDN no navegador do usuário.  
  
    -   **Sempre** preceder qualquer link de navegação com "Abrir" para que os usuários não ficará surpreso com navegado para algum outro conteúdo.  
  
    -   **Sempre** separar links de navegação de links úteis.  
  
#### <a name="ambient-indicators-optional"></a>Indicadores de ambiente (opcionais)  
 Indicadores de ambiente podem ser sutil, incluindo texto apresentado em uma cor contrastante do restante do código, ou óbvio, incluindo símbolos tickler como sublinhados rabisco e ícones de marca inteligente. Indicadores de ambiente se comunicar a disponibilidade de informações adicionais relevantes. Idealmente, eles fornecem informações úteis até mesmo sem que o usuário interagir com eles.  
  
-   **Sempre** posicionar um indicador de ambiente para que ele não atrapalhar ou sobrecarregar o usuário. Se for impossível para um ambiente indicador de posição de uma forma, considere a possibilidade de outra solução.  
  
-   **Sempre** posicionar o indicador de ambiente tão perto quanto possível ao que está relacionado ao conteúdo.  
  
-   **Sempre** tenta criar um indicador que resume as informações que ele disponibiliza. Considere fornecer uma contagem do número de itens de dados disponíveis (por exemplo, "3 referências" em vez de simplesmente "Referências") ou pensar em uma outra maneira de resumir os dados.  
  
    -   Em casos onde os dados para um indicador não podem sempre ser calculados e exibidos, considere imediatamente fornecendo feedback progressivo como os valores são calculados. Por exemplo, considere animando alterações que refletem as atualizações dos dados disponíveis, semelhantes à forma como o bloco dinâmico de email no Windows Phone é atualizada conforme o número de emails não lidos.  
  
-   **Nunca** adicionar indicadores de mais de um usuário pode realizar razoavelmente para uma determinada parte do conteúdo. Indicadores de ambiente devem ser útil sem exigir qualquer interação do usuário. Indicadores de perdem seu ambiente se precisam de estouro e outros controles de gerenciamento para colocá-los em modo de exibição.  
  
#### <a name="gestures"></a>Gestos  
 É um aspecto fundamental de permitir que o usuário manter o foco no conteúdo mestre, oferecendo suporte os gestos direito para abrir e fechar o conteúdo de detalhes adicionais.  
  
-   **Sempre** exigem que o usuário executar alguma gesto explícito para abrir o conteúdo adicional. Gestos abra comuns incluem:  
  
    -   **Focalizar:** dicas de ferramenta ou conteúdo informativo não interativo  
  
    -   **Comando explícito:** apresentador embutido  
  
    -   **Clique duas vezes no indicador de ambiente:** janela pop-up do CodeLens  
  
-   **Sempre** descartar o conteúdo de detalhes sempre que o usuário pressiona a tecla Esc.  
  
-   **Sempre** considerar o contexto da interface do usuário no objeto. Para conteúdo apresentadores que permitem a interação dentro do contêiner, considere cuidadosamente se deseja mostrar informações adicionais no foco, que é provável de ser perturbador para fluxo de trabalho do usuário.  
  
-   **Nunca** exibem conteúdo em foco que parece ser editável ou solicita a interação do usuário. Esse comportamento pode perturbar os usuários se eles tentarem move o cursor sobre o conteúdo de detalhes, como o comportamento padrão de uma dica de ferramenta é ignorar imediatamente quando o cursor não estiver mais sobre o mestre de conteúdo que produziu.  
  
##  <a name="a-namebkmkselectionmodelsa-selection-models"></a><a name="BKMK_SelectionModels"></a>Modelos de seleção  
  
### <a name="overview"></a>Visão Geral  
 Um modelo de seleção é o mecanismo usado para indicar e confirmar as operações em um ou mais objetos de interesse na interface do usuário. Este tópico aborda os padrões de interação de seleção nos editores de documento do Visual Studio: editores de texto, superfícies de design e modelagem superfícies.  
  
 Os usuários devem ter uma maneira de indicar para o Visual Studio que eles estão trabalhando e Visual Studio deve responder previsível com comentários aos usuários sobre o que está operando em. Diferenças ou um erro de comunicação entre o usuário e a interface do usuário pode resultar em usuário percebendo uma ação, que pode ter consequências indesejadas. Muitas vezes, o erro passa despercebido até que o usuário vê que algo está faltando ou foi alterada. Modelos de seleção são, portanto, uma das partes mais importantes de design da interface do usuário. Embora modelos de seleção no Visual Studio são consistentes com o Windows, existem pequenas variações.  
  
 No Visual Studio, como no Windows, os modelos de seleção diferem dependendo do contexto no qual ocorre a interação. Seleções podem ocorrer em quatro tipos de objetos:  
  
-   Texto  
  
-   Objetos gráficos  
  
-   Listas e árvores  
  
-   Grades  
  
 Nesses objetos, há três tipos de seleção:  
  
-   Contíguas  
  
-   Separação  
  
-   Região  
  
#### <a name="scope"></a>Escopo  
 O componente de seleção mais importante é garantir que o usuário sabe em qual janela estão trabalhando (ativação) e onde o foco está localizada (seleção). Visual Studio estende a funcionalidade de gerenciamento de janela no Windows, mas o esquema de ativação é o mesmo: interagir com uma janela coloca o foco para a janela. O Visual Studio tem dois indicadores para ativação: um para janelas de documento e outra para janelas de ferramenta.  
  
 Para janelas de documento, a janela ativa é indicada por uma guia de janela de documento chegando à frente e alterar sua cor de plano de fundo:  
  
 ![Seleção da guia ativa no Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713&01;_ActiveTab")  
  
 **Seleção da guia ativa**  
  
 Para janelas de ferramentas, a janela ativa é indicada por uma alteração na cor da área da barra de título da janela de ferramenta:  
  
 ![Seleção de janela de ferramenta ativas no Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713&02;_ActiveToolWindow")  
  
 **Janela da ferramenta ativa mostrando seleção principal de um nó**  
  
 ![Seleção de janela de ferramenta inativos no Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713&03;_InactiveToolWindow")  
  
 **Janela de ferramenta inativos, mostrando latente seleção de nó**  
  
 Depois que uma janela está ativa, seu foco é indicado acordo com os modelos de seleção descritos nesta seção das diretrizes.  
  
#### <a name="context"></a>Contexto  
 Visual Studio foi projetado para manter um conceito forte de contexto, controlar onde o usuário está trabalhando. Apenas uma janela está ativa, se ela for uma janela de ferramenta ou documento. No entanto, a janela de documento superior sempre retém uma seleção latente. Embora o foco pode estar em uma janela da ferramenta, a janela de documento que estava ativo pela última vez exibe uma seleção, até mesmo em um estado inativo. Isso é feito para manter o contexto do usuário no documento estava editando, mostrando que o Visual Studio manteve seu estado para que eles possam retornar e alternar facilmente entre janelas de ferramentas e janelas de documento.  
  
### <a name="text-selection"></a>Seleção de texto  
 Visual Studio editores são estritamente textuais, como o editor de texto interno, usam o mesmo modelo de seleção de texto e aparência descrito o [Mouse e ponteiros](https://msdn.microsoft.com/en-us/library/dn742466.aspx) página das diretrizes de interação de experiência de usuário do Windows no MSDN. O foco de entrada no editor de texto é indicado por uma barra vertical chamada o ponto de inserção. O ponto de inserção é um único pixel espesso e colorido como o inverso de tudo o que aparece por trás dele. Pisca acordo com a taxa definida **de intermitência do Cursor** definindo no **velocidade** guia o **teclado** miniaplicativo Painel de controle.  
  
#### <a name="contiguous-and-disjoint-selection"></a>Seleção contígua e separação  
 Seleção de dentro do editor de texto só é contígua. Texto seleções não são permitidas, mas devem ser abordadas nos editores de objeto gráfico de separação. Quando o ponteiro do mouse do usuário estiver sobre uma área de texto, o cursor muda a forma de i. Um único clique coloca o ponto de inserção no editor de texto no local do clique. Segurando o botão do mouse inicia um realce de seleção e liberar o botão do mouse termina o realce de seleção.  
  
#### <a name="region-selection-box-selection"></a>Seleção de região (seleção de caixa)  
 Visual Studio oferece suporte a seleções de região no editor de texto, e isso é chamado de seleção da caixa. Caixa de seleção permite que o usuário selecione uma região de texto que não segue o fluxo de texto normal. Assim como acontece com a seleção de texto padrão, a seleção deve ser contígua. Caixa de seleção é iniciada mantendo pressionada a tecla Alt enquanto arrasta o mouse. Caixa de seleção também pode ser iniciada, mantenha pressionada as teclas Shift e Alt ao usar as teclas de direção para indicar a região da seleção. Caixa de seleção usa o realce de seleção normal e mostra o cursor do ponto de inserção piscando no final da área de seleção.  
  
 ![Seleção de regionais (caixa) no Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713&04;_BoxSelection")  
  
 **Seleção de região (caixa) no Visual Studio**  
  
#### <a name="text-selection-appearance"></a>Aparência da seleção de texto  
 As cores usadas para seleção ativa e inativa no editor podem ser personalizadas. Para personalizar a aparência visual do editor, um usuário pode ir para **Ferramentas > opções**e, em seguida, procure **ambiente > fontes e cores > Editor de texto**.  
  
### <a name="graphical-selection"></a>Seleção de gráfica  
  
#### <a name="interaction"></a>Interação  
 Seleção de objetos gráficos pode ser complexa e depende de vários fatores:  
  
-   **Modelo de seleção principal do editor.** Editores que contêm objetos gráficos também podem ser usados para editar o texto ou grades. Por exemplo, o editor pode ser um editor de texto que também oferece suporte a colocação de objetos gráficos, como o designer do Visual Studio XAML. Suporte a vários tipos de objeto pode afetar como o usuário seleciona grupos compostos de diferentes tipos de objetos.  
  
-   **Suporte para estados de seleção primários e secundários.** Um editor pode fornecer seleção primária e secundária estados para que os objetos podem ser editados simultaneamente alinhados entre si, redimensionadas juntas, e assim por diante.  
  
-   **Suporte à edição in-loco.** Editores também podem permitir que o conteúdo de seus objetos de gráficos a ser editada. Por exemplo, uma forma de retângulo também pode conter texto interno que pode ser alterado pelo usuário. Além disso, esse texto pode ser centralizado ou justificado. Edição in-loco envolve um nível mais detalhado de interação do usuário e, portanto, requer um conjunto apropriado de visuais para apresentar informações de estado para o usuário.  
  
#### <a name="mouse-interaction"></a>Interação de mouse  
  
|Entrada|Resultado|  
|-----------|------------|  
|Clique em um objeto não selecionado|Seleciona o objeto e exibe uma linha tracejada e alças de seleção, se o objeto é redimensionado.|  
|Clique em um objeto selecionado|Ativa a edição in-loco, se o objeto oferecer suporte a ele. Clique fora do objeto desativa o modo de edição in-loco.|  
|Clique duas vezes em um objeto|Abre o código por trás do objeto para edição e pode inserir um manipulador de eventos padrão, se apropriado.|  
|Aponte para um objeto|Altera o ponteiro para o cursor de movimento. Pode alterar a aparência do objeto, como seu luminosidade ou cor.|  
|Aponte para uma alça de seleção|Altera o ponteiro para o cursor de redimensionamento. Para objetos que oferecem suporte a rotação, algumas alças de seleção podem alterar o ponteiro para um cursor de rotação conforme o ponteiro é posicionado diferente (por exemplo, movido para longe) em relação a alça de seleção.|  
|Arrastar|Mesmo se o objeto não for selecionado anteriormente, altera o ponteiro para o cursor de movimento e move o objeto.|  
|Editor perde o foco|Desativa o modo de edição in-loco, embora o objeto mantém o conteúdo e a aparência que tinha durante seu último estado de operação/seleção.|  
|Seleção de objetos|Indicado por uma borda, linha pontilhada ou outro tratamento visualmente distinto para realçar os limites do objeto.|  
|Redimensionar um objeto selecionado|Indicado por alças de seleção.<br /><br /> Um objeto redimensionável tem oito alças, representando cada direção na qual ele pode ser redimensionado. Menos identificadores podem ser usados se o objeto pode ser redimensionado apenas em determinadas instruções. Quando o usuário dimensiona um objeto até onde oito alças não é interativas, quatro identificadores podem ser usados. Tamanhos de identificador devem ser vinculados às métricas de borda e a borda de janela com o **GetSystemMetrics** função de API para tamanho proporcionalmente a resolução de vídeo.<br /><br /> ![Alças de redimensionamento](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|  
|Girar um objeto selecionado|![Alças de rotação](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713&06;_Rotate")|  
  
#### <a name="keyboard-interaction"></a>Interação do teclado  
  
|Entrada|Resultado|  
|-----------|------------|  
|Tabulação|Move o indicador de foco entre a ordem lógica dos objetos no editor. Isso pode ser esquerda para a direita ou de cima para baixo dependendo de **TabIndex** (ou equivalente) valor de propriedade, ordem de criação do objeto e o objetivo geral do editor. Shift + Tab inverte a direção do indicador de foco.|  
|Barra de espaços|Ativa o modo panorâmica enquanto o pressionamento de tecla é mantido. Entrada de mouse adicional é necessária para deslocar a posição do visor.|  
|Ctrl+Barra de espaços|Ativa o modo de zoom enquanto o pressionamento de tecla é mantido. Entrada de mouse adicional é necessária para aumentar ou diminuir o fator de zoom.|  
|Ctrl + Alt + sinal de subtração|Diminui o fator de zoom em um nível.|  
|Ctrl + Alt + sinal de adição|Aumenta o fator de zoom em um nível.|  
|Ctrl ou SHIFT|Adiciona o objeto para o grupo de seleção. CTRL também permite que você remova objetos individualmente a partir do grupo de seleção.|  
|Entrar|Executa o comando padrão para o objeto (geralmente abrir ou editar).|  
|F2|Ativa a edição in-loco para o objeto.|  
|Teclas de direção|Move os objetos selecionados na direção da tecla pressionada, em pequenos incrementos (por exemplo, 1 pixel por vez)|  
|CTRL + teclas de direção|Move os objetos selecionados na direção da tecla pressionada, em incrementos maiores (por exemplo, 10 pixels por vez)|  
|SHIFT + seta para chaves|Redimensiona os objetos selecionados na respectiva direção, em pequenos incrementos (por exemplo, 1 pixel por vez)|  
|Ctrl + Shift + teclas de direção|Redimensiona os objetos selecionados na respectiva direção, em incrementos maiores (por exemplo, 10 pixels por vez)|  
  
 Quando os usuários editar controles em vigor, pode fazer sentido para os objetos para redimensionar automaticamente com a entrada do usuário. Por exemplo, se o usuário edita um controle de rótulo, o rótulo deve aumentar para exibir o texto que o usuário acabou de digitar. Se isso não for feito, o usuário deve redimensionar o controle manualmente depois de editar o texto. Se o usuário tem muitos controles, isso se torna um atividades rotineiras e tarefa improdutiva.  
  
#### <a name="graphical-containers"></a>Contêineres de gráficos  
 Em alguns casos, editores gráficos fornecem contêineres para outros objetos gráficos, como o controle de painel Windows Forms ou o controle de Layout de grade no designer de HTML. Se o editor fornece contêineres para outros objetos gráficos, o modelo de seleção a seguir deve ser usado para o contêiner somente (objetos dentro o acompanhamento do contêiner do modelo padrão, como descrito acima):  
  
|Entrada|Resultado|  
|-----------|------------|  
|Clique no contêiner|Seleciona o objeto de contêiner sem selecionar qualquer um dos objetos contidos diretamente. O contêiner pode movido e/ou redimensionado com padrão do mouse e teclado (como descrito acima). Objetos contidos são movidos em relação ao contêiner, mas os objetos contidos não são redimensionados, a menos que elas são selecionadas diretamente.|  
|Passe o mouse sobre a região de limites do contêiner|Ativa o mouse para o cursor de movimento, indicando que o contêiner pode ser movido.|  
|Arraste a região de limites do contêiner|Altera o mouse para o cursor de movimento e move o contêiner (e os objetos contidos em). O contêiner não pode ser movido sem primeiro selecionado com um único clique.|  
|Clique em um objeto dentro do contêiner|Desmarca o contêiner (se estiver selecionada) e seleciona apenas o objeto clicado.|  
|SHIFT + clique ou Ctrl + clique em um objeto contido e/ou contêiner|Adiciona o objeto clicado para um grupo de seleção ou uma seleção existente. Se o objeto clicado já for um membro do grupo de seleção, ele será removido do grupo de seleção.|  
  
 Os objetos contidos devem seguir o modelo básico de seleção conforme descrito na seção anterior. Com o teste de usabilidade do Windows Forms designer, usuários esperado acesso contínuo aos objetos contidos sem etapas intermediárias (impostas pelo objeto de contenção).  
  
#### <a name="disjoint-and-region-selections"></a>Separação e seleções de região  
 Editores de objeto gráfico devem dar suporte a seleções não contíguas. Observe que esse gráfico não mostra a aparência do controle para o Visual Studio. Consulte [aparência da seleção de objeto gráfico](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) para especificações detalhadas de visual.  
  
 ![Separação e seletores de região](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713&07;_DisjointRegionSelectors")  
  
 **Seleção de separação**  
  
 Editores gráficas também devem fornecer as seleções de região com um indicador de seleção do tipo de marca de seleção. Se o editor gráfico oferece suporte a outros tipos de objeto (como texto), seleções de região não seria possíveis dependendo das restrições desses outros tipos de objeto.  
  
 ![Marca de seleção](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713&08;_MarqueeSelection")  
  
 **Marca de seleção**  
  
#### <a name="primary-and-secondary-selections"></a>Seleções primárias e secundárias  
 Alguns editores de objeto gráfico permitem ao usuário editar ou alinhar objetos em grupos. Nesse caso, o conceito de seleções primários e secundários precisa ser introduzido. A seleção principal é o objeto ao qual todos os outros objetos respondem por operações de grupo. O objeto que o usuário seleciona primeiro se torna o controle principal e as seleções secundárias se tornam seleções subsequentes. A seleção principal tem um tratamento visual distinto das seleções secundários para indicar qual objeto primário:  
  
 ![Seleção primária e secundária](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713&09;_PrimarySecondary")  
  
 **Seleção principal com duas seleções secundárias**  
  
####  <a name="a-namebkmkgraphicalobjectselectionappearancea-graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Aparência da seleção de objeto gráfico  
 As alças de seleção são desenhados em um padrão retangular ao redor da caixa delimitadora do objeto de quadrados. O gráfico a seguir mostra exemplos de vários estados que um objeto gráfico pode ter com a alça de dimensionamento e aparência de edição in-loco. O tamanho das alças deve estar vinculado a borda da janela e métricas de borda usando o **GetSystemMetrics** API.  
  
|Estado|Aparência|Detalhes visuais|  
|-----------|----------------|--------------------|  
|**Não selecionada**|Padrão|![Estado do botão padrão](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713&10;_DefaultState")||  
|**Seleção principal**|Redimensionáveis|![Seleção principal com alças de redimensionamento](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713&11;_PrimaryResize")|![Seleção principal com Redimensionar alças (ampliadas)](../../extensibility/ux-guidelines/media/0713-12_primaryresizezoom.png "0713&12;_PrimaryResizeZoom")|  
|**Seleção principal**|Não redimensionáveis|![Alças de redimensionamento de seleção principal sem](~/docs/extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713&13;_PrimaryNoResize")|![Seleção principal sem redimensionar alças (ampliadas)](../../extensibility/ux-guidelines/media/0713-14_primarynoresizezoom.png "0713&14;_PrimaryNoResizeZoom")|  
|**Seleção principal**|Bloqueado|![Seleção principal bloqueada](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713&15;_PrimaryLocked")|![Seleção principal bloqueado (com zoom)](../../extensibility/ux-guidelines/media/0713-16_primarylockedzoom.png "0713&16;_PrimaryLockedZoom")|  
|**Seleção secundária**|Redimensionáveis|![Seleção secundária com alças de redimensionamento](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713&17;_SecondaryResize")|![Seleção secundária com Redimensionar alças (ampliadas)](~/docs/extensibility/ux-guidelines/media/0713-18_secondaryresizezoom.png "0713&18;_SecondaryResizeZoom")|  
|**Seleção secundária**|Não redimensionáveis|![Alças de redimensionamento de seleção secundária sem](~/docs/extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713&19;_SecondaryNoResize")|![Seleção secundária sem redimensionamento (ampliado)](~/docs/extensibility/ux-guidelines/media/0713-20_secondarynoresizezoom.png "0713&20;_SecondaryNoResizeZoom")|  
|**Seleção secundária**|Bloqueado|![Seleção secundária bloqueada](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713&21;_SecondaryLocked")|![Seleção secundária bloqueada (com zoom)](../../extensibility/ux-guidelines/media/0713-22_secondarylockedzoom.png "0713&22;_SecondaryLockedZoom")|  
|**Interface do usuário ativo**|Padrão|![Estado ativo da interface do usuário](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713&23;_UIActive")|![Estado ativo de interface do usuário (ampliado)](../../extensibility/ux-guidelines/media/0713-24_uiactivezoom.png "0713&24;_UIActiveZoom")|  
  
### <a name="view-selection-models"></a>Modelos de seleção de exibição  
  
#### <a name="tree-view"></a>Exibição de árvore  
 Seleção em uma exibição de árvore é mostrada com um realce simple. Se o usuário clica em um nome de nó ou um ícone de nó, o nó fica selecionado. Os glifos triangulares à esquerda do nó expandir ou contrair o controle de árvore mas não afetam a seleção do usuário, com uma exceção: ao recolher um nó pai quando a seleção está em um filho do nó, a seleção se move para o pai.  
  
 ![Modo de exibição de árvore típico no Visual Studio](~/docs/extensibility/ux-guidelines/media/0713-25_treeview.png "0713&25;_TreeView")  
  
 **Modo de exibição de árvore típico no Visual Studio**  
  
 Modos de exibição de árvore podem dar suporte a seleções contíguas e separadas, mesmo entre vários níveis na árvore. Contíguo ou não contíguo várias seleções devem ser feitas em nós de árvore visível. Se um nó estiver recolhido, a seleção de separação é perdida e o nó que foi recolhido obtém a seleção. Dessa forma, o usuário pode ver os nós que serão afetados por uma operação. Quando nós são recolhidos, fica claro que nós podem ser afetados.  
  
 Quando um nó pai é selecionado, a operação deverá aplicar o pai, embora possa haver casos em que faz sentido para uma operação aplicar ao pai e todos os seus filhos. Nesse caso, fornece adicional da interface do usuário durante a operação, como uma caixa de seleção ou caixa de diálogo de confirmação para tornar a opção "aplicar a todos os filhos" explícita para o usuário.  
  
##### <a name="renaming"></a>Renomeando  
 Se nós da árvore oferece suporte à renomeação, renomeando deve ser feito no local. A operação em andamento deve ser o padrão em todos os controles de árvore no Visual Studio. Forneça um comando rename que ativa imediatamente o modo de edição in-loco, com a seleção de texto que abrangem o nome completo do nó, pronto para aceitar a entrada do usuário. Se o nó representa um arquivo, o nome do arquivo deve conter a extensão. O realce de seleção deve incluir somente o corpo de nome de arquivo e não a extensão.  
  
|Entrada|Resultado|  
|-----------|------------|  
|Tecla Enter|Confirma a operação de renomeação|  
|Tecla ESC|Cancela a operação de renomeação|  
|Clique fora da região de edição in-loco|Confirma a operação de renomeação|  
|Desfazer|Fornecer fácil desfazer para cancelar a operação de renomeação|  
  
#### <a name="selection-within-lists-and-grid-controls"></a>Seleção em listas e controles de grade  
 O principal conceito na seleção de lista é que ele é baseado em linha, que significa que quando uma seleção é feita a linha inteira é selecionado como uma unidade. Por outro lado, grades podem permitir a células específicas para ser selecionado sem afetar qualquer outro aspecto da linha. Grades também podem conter uma hierarquia de linhas aninhadas (como em uma grade de árvore) que permitem que todo ramificações da hierarquia a ser marcada e desmarcada interagindo com as linhas pai. Seleção na lista é representada por uma cor de realce simples em toda a linha de dados. O foco é mostrado por uma borda pontilhada de pixel único ao redor da linha atual de editável ou célula (linha se todas as células são somente leitura).  
  
> [!NOTE]
>  **Foco** e **seleção** são conceitos diferentes. *Foco* é uma indicação de qual interface do elemento é destinado para receber entrada dirigida não explicitamente a outro objeto, enquanto *seleção* se refere ao estado da inclusão de um objeto em um conjunto de objetos nos quais podem ocorrer operações subsequentes.  
  
 As seleções nas listas podem ser contíguas, separado, ou região. Quando várias seleções são permitidos, contíguas e seleção disjunção sempre deve ter suporte, embora o suporte para opções de região (caixa) são opcional. Seleções de região são iniciadas, arrastando o espaço em branco do corpo da lista.  
  
|Objeto|Seleção|  
|------------|---------------|  
|Lista|Contíguas|Sempre tem suporte (quando várias seleções são permitidas).|  
|Lista|Separação|Sempre tem suporte (quando várias seleções são permitidas).|  
|Lista|Região|Suporte opcional. Iniciada arrastando o mouse espaço em branco do corpo da lista.|  
  
 Clicar uma vez em uma lista seleciona a linha onde ocorreu o clique. Se o usuário clicar em uma célula da lista que dá suporte à edição in-loco, a célula logo é ativada para edição in-loco. Caso contrário, a linha inteira é imediatamente marcada e mostra um realce.  
  
 Arrastando no corpo da lista faz uma das três coisas:  
  
-   Inicia uma seleção de região, se a lista dá suporte a ela e o mouse para baixo no espaço em branco  
  
-   Inicia uma operação de arrastar/soltar se a lista de célula ou linha dá suporte a uma fonte de arrastar  
  
-   Seleciona a linha atual  
  
##### <a name="in-place-editing"></a>Edição in-loco  
 Quando é permitido edição in-loco, há dois modelos básicos: Seletor de propriedade e controle de edição simples. Com um controle de edição simples, o conteúdo é realçado e pronto para o usuário de entrada como edição in-loco é ativado. Quando um seletor de propriedade é implementado, o botão que invoca o seletor de propriedade é exibido depois que o modo de edição in-loco é ativado e a seleção atual não é realçada. Botão seletor deve ser justificado à direita da célula. Para obter exemplos de edição in-loco, consulte o **janela propriedades** e **lista de tarefas** no Visual Studio.  
  
##### <a name="keyboard-support"></a>Suporte de teclado  
 Suporte de teclado para a seleção em listas e grades segue as convenções padrão do Windows:  
  
-   Teclas de seta para navegar pela lista, selecionando cada célula da linha/como o foco é movido.  
  
-   SHIFT + seta executa uma seleção contígua na direção das teclas de direção.  
  
-   CTRL + seta seguido de barra de espaço alterna entre adicionando e removendo itens de lista de seleção, criando uma seleção separada.  
  
-   Para grades que contenham hierarquias aninhadas, a tecla de seta para a direita expande uma linha pai e a tecla de seta para a esquerda recolhe um.  
  
-   A tecla Tab move o foco entre as células na linha atual, se as células são editáveis.  
  
-   A tecla Enter executa o comando padrão no item na lista (geralmente **abrir**).  
  
-   A tecla F2 ativa a edição in-loco para a célula selecionada no momento.  
  
##  <a name="a-namebkmkpersistenceandsavingsettingsa-persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Persistência e salvar as configurações  
  
### <a name="overview"></a>Visão Geral  
 Embora cada componente de software no Visual Studio é geralmente responsável por seu próprio estado e persistência, o Visual Studio automaticamente salva as configurações em alguns casos, como com posições e tamanhos de janela. A tabela a seguir é uma combinação de configurações salvas automaticamente e que exigem um usuário explícito ou programados ação a ser executada.  
  
|Objeto|O que salvar|Quando salvar|Onde salvar|  
|------------|------------------|------------------|-------------------|  
|Objeto selecionável (por exemplo, uma linha de código)|Um ponto de interrupção em uma linha de código<br /><br /> Um atalho de usuário associado à linha de código|Quando o projeto é salvo|O **opções do usuário (. suo)** arquivo do projeto|  
|Caixa de Diálogo|O local da caixa de diálogo, se ele tiver sido movido<br /><br /> O modo de exibição que o usuário usado por último na caixa de diálogo|Quando a caixa de diálogo é fechada<br /><br /> Quando termina a sessão do Visual Studio|Na memória<br /><br /> Registro em **HKEY_Current_User**|  
|Janela|O tamanho e o local da janela|Quando a janela é fechada<br /><br /> Quando o modo do Visual Studio for alterado<br /><br /> Quando termina a sessão do Visual Studio|O **opções do usuário (. suo)** arquivo do projeto<br /><br /> Arquivo de opções personalizadas para as configurações da janela|  
|Documento|A seleção atual no documento<br /><br /> O modo de exibição do documento<br /><br /> Os último vários lugares que o usuário visitou|Quando o documento é salvo|O **opções do usuário (. suo)** arquivo do projeto|  
|Projeto|Referências a arquivos<br /><br /> Referências a diretórios no disco<br /><br /> Referências a outros softwares<br /><br /> Componentes<br /><br /> Informações de estado sobre o projeto em si|Quando o projeto é salvo|O arquivo de projeto|  
|Solução|Referências a projetos<br /><br /> Referências a arquivos|Quando a solução ou projeto é salvo|O **solução (. sln)** arquivo|  
|As configurações no **Ferramentas > opções**|Personalizações de teclado<br /><br /> Personalizações da barra de ferramentas<br /><br /> Esquemas de cores|Quando o **Ferramentas > opções** caixa de diálogo é fechada<br /><br /> Quando termina a sessão do Visual Studio|Registro em **HKEY_Current_User**|  
  
 O que o usuário está fazendo e quando eles estão fazendo, determina se uma configuração está sendo salvo na memória (durante a sessão), salva em disco (em sessões como uma configuração de registro), como parte do projeto ou solução de arquivo em si, como parte do **opções de solução (. sln)** de arquivos, ou como um configurações personalizadas de arquivos que somente esse componente de software conhecem. A tabela acima mostra vários eventos no qual é possível salvar as configurações. No entanto, existem outras ocasiões em que deseja salvar o estado:  
  
-   Quando o usuário altera o local dentro de uma caixa de diálogo ou janela  
  
-   Quando o usuário transfere o foco para outra janela  
  
-   Quando o usuário alterna do design para o modo de depuração  
  
-   Quando o usuário fizer logoff da sua conta  
  
-   Quando o computador entra em hibernação ou desligado  
  
-   Quando o computador/disco rígido está prestes a ser reformatado e configurar novamente  
  
### <a name="window-configurations"></a>Configurações de janela  
 Uma configuração de janela é a apresentação básica do ambiente de desenvolvimento – é um esquema consiste em lista de janelas de ferramentas presentes e a maneira na qual eles estão organizados. Windows gerenciado pelo IDE (janelas do IDE), informações de layout são mantidas por usuário, para que quando um usuário inicia o IDE, o layout da janela é exibida mesmo que quando eles último encerrou o Visual Studio. O estado e a posição das janelas do IDE é mantida em um arquivo de opções personalizadas no formato XML. Janelas de ferramentas que são criadas por pacotes carregados no IDE manter suas informações de estado no registro e podem ou não ser por usuário.  
  
#### <a name="profile-specific-layouts"></a>Layouts específicos de perfil  
 Cada perfil inclui layouts de janela da ferramenta, organizados de forma familiar para personas de desenvolvedor específica (os desenvolvedores de Visual C++ esperam ver o **Solution Explorer** no lado esquerdo do IDE, enquanto os desenvolvedores do c# esperam ver o **Solution Explorer** à direita). Layouts de janela específico para o perfil são carregados depois que o usuário escolhe um perfil na inicialização. Um autor de pacote deve determinar o layout da janela mais adequado para a experiência de seus clientes, sabendo que as alterações feitas pelo usuário para a configuração de janela, em seguida, serão persistentes.  
  
##  <a name="a-namebkmktouchinputa-touch-input"></a><a name="BKMK_TouchInput"></a>Entrada por toque  
 Os usuários estão usando cada vez mais produtos de desenvolvimento Microsoft em dispositivos de toque. No entanto, há barreiras que dificultam a usar ferramentas de desenvolvimento em dispositivos de toque. Os usuários esperam nossos produtos para fornecer uma experiência de toque precisos e confiáveis. O objetivo dessas diretrizes é informar decisões sobre quais recursos de toque para incorporar e incentivar uma experiência consistente de toque em Visual Studio e produtos relacionados.  
  
### <a name="levels-of-experience"></a>Níveis de experiência  
 Os seguintes níveis de experiência destinam-se a servir como um guia para ajudar as equipes a decidir quais recursos de toque para oferecer com base em seu nível desejado de interesse de investimento em contato.  
  
-   O **experiência básica** para equipes que desejam fornecer recursos de toque portanto não há nenhum ineficiência em todo o seu trabalho.  
  
-   O **otimização experiência** para equipes que desejem fornecer mais recursos de toque comum (por exemplo, aqueles normalmente disponíveis em aplicativos de navegador da internet).  
  
-   O **elevados experiência** é para equipes que desejam adicionar recursos tais como gestos ou outros recursos opcionais que podem tornar seus aplicativos touch-first amigável.  
  
||Experiência básica|Experiência otimizada|Experiência com privilégios elevados|  
|-|----------------------|--------------------------|-------------------------|  
|Permite aos usuários...|Corrija o código e solução/projeto no nível de leitura sem ineficiência|Executar tarefas de manutenção, refatora e navegação|Operar em uma experiência consistente, intuitiva e flexível com confiança|  
|Editor|Panorâmica de toque e seleção<br /><br /> Toque ScrollBar saltar e pressione + arrastar|Segure o zoom<br /><br /> Rolagem rápida<br /><br /> Seleção<br /><br /> Fácil de usar do menu de contexto||  
|Janelas de ferramentas superior|Lista de movimento panorâmico<br /><br /> Seleção de item<br /><br /> Toque ScrollBar saltar e pressione + arrastar|Seleção e fácil item de rolagem||  
|Janelas||Redimensionar a janela<br /><br /> Acesso rápido||  
|Documento bem||Navegação fácil entre arquivos abertos||  
|Gestos||Certifique-se de gestos comuns trabalhar no IDE|Ações de gestos<br /><br /> Suporte a arrastar-e-soltar e designers|  
|Outras considerações|||Teclado na tela personalizado|  
  
#### <a name="gestures"></a>Gestos  
 Gestos de fornecem aos usuários um atalho para comandos que caso contrário, podem exigir uma interação mais complicada. Consulte as diretrizes do Windows em [gestos de toque comum para aplicativos de área de trabalho](http://msdn.microsoft.com/en-us/library/windows/desktop/dd940543\(v=vs.85\).aspx)e siga este guia para a maioria dos gestos, incluindo gestos simples, como Panorâmica e zoom.
