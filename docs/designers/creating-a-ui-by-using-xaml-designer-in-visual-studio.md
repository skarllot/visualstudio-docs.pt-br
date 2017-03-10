---
title: "Criando uma interface de usu&#225;rio usando o XAML Designer no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.XamlDesigner"
  - "VS.DevicePanel"
  - "VS.XamlEditor"
  - "VS.DocumentOutline"
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
caps.latest.revision: 29
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Criando uma interface de usu&#225;rio usando o XAML Designer no Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Designer XAML no Visual Studio fornece uma interface visual para ajudá\-lo a criar aplicativos da Windows Store, Windows Phone, WPF e Silverlight baseados em XAML. Você pode criar interfaces de usuário para seus aplicativos, arrastando controles a partir de **Toolbox** e definindo propriedades no **propriedades** janela. Você também pode editar XAML diretamente no modo de exibição XAML.  
  
 Para tarefas avançadas de design XAML como animações e comportamentos, consulte [Criando uma interface de usuário usando o Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).  
  
## Espaço de trabalho do Designer XAML  
 O espaço de trabalho no Designer XAML consiste em vários elementos de interface visual. Isso inclui a prancheta, o Editor XAML, janela de dispositivo, a janela estrutura de tópicos do documento e a janela Propriedades. Para abrir o Designer XAML, clique em um arquivo XAML no **Solution Explorer** e escolha **View Designer**.  
  
## Criando modos de exibição  
 O Designer XAML fornece um modo de exibição XAML e um modo Design sincronizado de marcação XAML renderizada de seu aplicativo. Com um arquivo XAML aberto no Visual Studio, você pode alternar entre XAML e modo de Design usando o **Design** e **XAML** guias. Você pode usar o botão **Alternar Painéis** para alternar qual janela é exibida no topo: o artboard ou o Editor XAML.  
  
 No modo Design, a janela que contém o *artboard* é a janela ativa. Você pode usá\-la como superfície de trabalho primária. Você pode usá\-la para criar visualmente uma página em seu aplicativo adicionando ou desenhando elementos e depois modificando\-os. Para saber mais, veja [Trabalhando com elementos no Designer XAML](../designers/working-with-elements-in-xaml-designer.md). Esta ilustração mostra o artboard no modo Design.  
  
 ![Modo de design do Designer XAML](../designers/media/xaml_editor_design_view.png "xaml\_editor\_design\_view")  
  
 Estas funcionalidades estão disponíveis no artboard:  
  
 **Guias de alinhamento**  
 Guias de alinhamento são *limites de alinhamento* que aparecem como linhas tracejadas vermelho para mostrar quando as bordas dos controles são alinhadas, ou quando as linhas de base de texto são alinhadas. Os limites de alinhamento só são exibidos quando a opção de **ajuste a guias de alinhamento** está habilitada.  
  
 **Rails de grade**  
 `Grid` trilhos são usados para gerenciar linhas e colunas em um [grade](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) painel. Você pode criar e excluir linhas e colunas, bem como ajustar suas larguras e alturas relativas. Suporte de grade vertical aparece à esquerda da prancheta, é usada para linhas e a linha horizontal, que aparece na parte superior, é usada para colunas.  
  
 **Adornos de grade**  
 Um adorno `Grid` é exibido como um triângulo que tem uma linha vertical ou horizontal anexada a ele no rail `Grid`. Quando você arrasta um adorno `Grid`, as larguras ou alturas das linhas ou colunas adjacentes são atualizadas enquanto o mouse é movimentado.  
  
 Os adornos `Grid` são usados para controlar a largura e altura das linhas e colunas de uma `Grid`. Você pode adicionar uma nova coluna ou linha clicando nos rails de `Grid`. Quando você adiciona uma nova linha ou linha de coluna a um painel `Grid` que possui duas ou mais colunas ou linhas, uma minibarra de ferramentas exibida fora do rail permite definir explicitamente a largura e a altura. A Minibarra de ferramentas permite que você defina opções de dimensionamento para `Grid` linhas e colunas.  
  
 **Alças de redimensionamento**  
 As alças de redimensionamento são exibidas em controles selecionados e permitem redimensionar o controle. Quando você redimensiona um controle, os valores de largura e altura geralmente são exibidos para ajudar a dimensionar o controle. Para saber mais sobre a manipulação de controles no modo Design, veja [Trabalhando com elementos no Designer XAML](../designers/working-with-elements-in-xaml-designer.md).  
  
 **Margens**  
 As margens representam o espaço fixo entre a borda de um controle e a borda do respectivo contêiner. Você pode definir as margens de um controle usando o [margem](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) propriedades em **Layout** na janela Propriedades.  
  
 **Adornos de margem**  
 Você pode usar adornos de margem para alterar as margens de um elemento relativo ao respectivo contêiner de layout. Quando um adorno de margem está aberto, uma margem não está definida, e o adorno de margem exibe uma cadeia quebrada. Quando a margem não está definida, os elementos permanecem no lugar quando o contêiner de layout é redimensionado em tempo de execução. Quando um adorno de margem está fechado, um adorno de margem exibe uma cadeia ininterrupta, e os elementos são movidos com a margem enquanto o contêiner de layout é redimensionado em tempo de execução \(a margem permanece fixa\).  
  
 **Alças do elemento**  
 Você pode modificar um elemento usando as alças do elemento que são exibidas no artboard ao mover o ponteiro sobre os cantos da caixa azul que circunda um elemento. Essas alças permitem girar, redimensionar, inverter, mover ou adicionar um radiano do canto ao elemento. O símbolo da alça do elemento varia por função e altera dependendo do local exato do ponteiro. Se você não vir as alças do elemento, verifique se o elemento está selecionado.  
  
 No modo Design, os comandos adicionais do artboard estão disponíveis na área esquerda inferior da tela, como mostrado aqui:  
  
 ![Comandos do modo de exibição Design](../designers/media/xaml_editor_design_controls.png "xaml\_editor\_design\_controls")  
  
 Estes comandos estão disponíveis na barra de ferramentas:  
  
 **Zoom**  
 O zoom permite dimensionar a superfície de design. Você pode aplicar zoom de 12,5% a 800% ou selecionar opções, como **Ajustar à Seleção** e **Ajustar a Tudo**.  
  
 **Grade de ajuste Mostrar\/Ocultar**  
 Exibe ou oculta a grade de ajuste que mostra as linhas de grade. As linhas de grade são usadas quando a opção de **ajuste a linhas de grade** ou de **ajuste a guias de alinhamento** está habilitada.  
  
 **Ativar\/desativar ajuste às linhas de grade**  
 Se a opção de **ajuste às linhas de grade** estiver habilitada quando você arrastar um elemento no artboard, a tendência será o elemento alinhar\-se às linhas de grade horizontais e verticais mais próximas.  
  
 **Ativar\/desativar ajuste às guias de alinhamento**  
 As guias de alinhamento ajudam a alinhar os controles relativos uns aos outros. Se a opção de **ajuste às guias de alinhamento** estiver habilitada, quando você arrastar um controle relativo a outros controles, os limites de alinhamento serão exibidos quando as margens e o texto de alguns controles estiverem alinhados horizontal ou verticalmente. Um limite de alinhamento é exibido como uma linha vermelho\-tracejada.  
  
 No modo de exibição XAML, a janela que contém o editor XAML é a janela ativa, e o editor XAML é a ferramenta de criação primária. A linguagem XAML fornece um vocabulário declarativo, com base em XML, para especificar a interface do usuário de um aplicativo. O modo de exibição XAML inclui o IntelliSense, formatação automática, realce de sintaxe e navegação de marcação. Esta ilustração mostra o modo de exibição XAML:  
  
 ![Modo de exibição XAML](../designers/media/xaml_editor.png "xaml\_editor")  
  
 **Barra do modo divisão**  
 A barra do modo divisão é exibida na parte superior do modo de exibição XAML quando o editor XAML está na janela inferior. A barra do modo divisão permite controlar os tamanhos relativos do modo Design e do modo de exibição XAML. Você também pode trocar os locais dos modos de exibição \(usando o botão **Alternar Painéis**\), especificar se os modos de exibição são organizados horizontal ou verticalmente e recolher o modo de exibição.  
  
 **Zoom de marcação**  
 O zoom de marcação permite dimensionar o modo de exibição XAML. Você pode aplicar zoom de 20% a 400%.  
  
## Janela Dispositivo  
 A janela do dispositivo no Designer XAML permite simular em tempo de design várias exibições, exibições e opções de exibição para seu projeto da Windows Store ou Windows Phone. A janela Dispositivo está disponível no menu **Design** quando você está trabalhando no XAML Designer. Veja como ela se parece:  
  
 ![Janela do dispositivo](../designers/media/xaml_editor_device_panel.png "xaml\_editor\_device\_panel")  
  
 Estas são as opções disponíveis na janela Dispositivo:  
  
 **Vídeo**  
 Especifica diferentes resoluções e tamanhos de exibição para o aplicativo.  
  
 **Orientação**  
 Especifica diferentes orientações para o aplicativo: **Paisagem** ou **Retrato**.  
  
 **Microsoft Edge**  
 Especifica diferentes alinhamentos de borda para o aplicativo: **Ambos**, **Esquerda**, **Direita** ou **Nenhum**.  
  
 **Alto Contraste**  
 Visualize o aplicativo com base na configuração de contraste selecionada. Essa configuração, quando definida como um valor diferente do valor **Padrão**, substituirá a propriedade `RequestedTheme` definida no arquivo App.xaml.  
  
 **Substituir colocação em escala**  
 Ativa e desativa a emulação da colocação de documento em escala na superfície de design. Isso permite aumentar o percentual de colocação em escala por um fator. Marque a caixa de seleção para ativar a emulação. Por exemplo, se o percentual de colocação em escala for de 100%, o documento na superfície de design será dimensionado em até 140%. Essa opção será desabilitada se o percentual de colocação em escala atual for de 180.  
  
 **Largura mínima**  
 Especifica a configuração de largura mínima. A largura mínima pode ser alterada em App.xaml.  
  
 **Tema**  
 Especifica o tema do aplicativo. Por exemplo, você pode alternar entre um escuro e um tema no claro.  
  
 **Mostrar cromado**  
 Ativa ou desativa o quadro de tablet simulado em torno do aplicativo no modo Design. Marque a caixa de seleção para mostrar o quadro.  
  
 **Recortar para exibir**  
 Especifica o modo de exibição. Marque a caixa de seleção para recortar o tamanho do documento de acordo com o tamanho do vídeo.  
  
## Janela Estrutura de Tópicos de Documento  
 A janela Estrutura de Tópicos de Documento no Designer XAML ajuda a executar estas tarefas:  
  
-   Exibir a estrutura hierárquica de todos os elementos no artboard.  
  
-   Selecionar elementos para que você possa modificá\-los \(movê\-los na hierarquia, modificá\-los no artboard, definir suas propriedades na janela Propriedades e assim por diante\). Para saber mais, veja [Trabalhando com elementos no Designer XAML](../designers/working-with-elements-in-xaml-designer.md).  
  
-   Criar e modificar modelos para elementos que são controles.  
  
-   Usar o menu de contexto para elementos selecionados. O mesmo menu também está disponível para os elementos selecionados no artboard.  
  
 Para exibir a janela de estrutura de tópicos do documento, na barra de menus, escolha **exibição**, **outras janelas**, **Document Outline**.  
  
 ![Janela Document Outline](../designers/media/xaml_editor_doc_outline.png "xaml\_editor\_doc\_outline")  
  
 Estas são as opções disponíveis na janela de estrutura de tópicos do documento:  
  
 **Estrutura de Tópicos do Documento**  
 O modo de exibição principal na janela Estrutura de Tópicos de Documento exibe a hierarquia de um documento em uma estrutura de árvore. Você pode usar a natureza hierárquica da estrutura de tópicos de documento para examinar o documento em vários níveis de detalhes, bem como para bloquear e ocultar os elementos individualmente ou em grupos.  
  
 **Mostrar\/ocultar**  
 Exibe ou oculta os elementos do artboard que correspondem aos itens na Estrutura de Tópicos de Documento. Use os botões **Mostrar\/Ocultar**, que exibem um símbolo de olho quando mostrados, ou pressione CTRL\+H para ocultar elementos e SHIFT\+CTRL\+H para exibi\-los.  
  
 **Bloquear\/desbloquear**  
 Bloqueia ou desbloqueia os elementos do artboard que correspondem aos itens na Estrutura de Tópicos de Documento. Os elementos bloqueados não podem ser modificados. Use os botões **Bloquear\/desbloquear**, que exibem um símbolo de cadeado quando bloqueados, ou pressione CTRL\+L para bloquear elementos e SHIFT\+CTRL\+L para desbloqueá\-los.  
  
 **Retornar escopo para pageRoot**  
 A opção na parte superior da janela Estrutura de Tópicos de Documento, que mostra um símbolo de seta para cima, retorna a estrutura de tópicos de documento ao escopo anterior. O controle de escopo só é aplicável quando você está no escopo de um estilo ou modelo.  
  
## Janela de Propriedades  
 A janela Propriedades permite definir valores de propriedade em controles. Veja como ela se parece:  
  
 ![Janela Propriedades](../designers/media/xaml_editor_prop_window.png "xaml\_editor\_prop\_window")  
  
 Há várias opções na parte superior da janela Propriedades. Você pode alterar o nome do elemento atualmente selecionado usando a caixa **Nome**. No canto esquerdo superior, há um ícone que representa o elemento atualmente selecionado. Para organizar as propriedades por categoria ou em ordem alfabética, clique em **Categoria**, **Nome** ou **Fonte** na lista **Organizar por**. Para ver a lista de eventos de um controle, clique no botão **Eventos**, que exibe um símbolo de relâmpago. Para procurar uma propriedade, comece a digitar o nome da propriedade no **Propriedades de pesquisa** caixa. A janela Propriedades exibe as propriedades que correspondem à pesquisa à medida que você digita. Algumas propriedades permitem que você defina propriedades avançadas selecionando um botão de seta para baixo. Para obter mais informações sobre como usar propriedades e manipulação de eventos, consulte [início rápido: adicionando controles e manipulando eventos](http://go.microsoft.com/fwlink/?LinkID=247983)  
  
 À direita de cada valor de propriedade está um *marcador de propriedade* que é exibido como símbolo de caixa. A aparência do marcador da propriedade indica se existe uma associação de dados ou um recurso aplicado à propriedade. Por exemplo, um símbolo de caixa branca indica um valor padrão, um símbolo de caixa preta normalmente indica que um recurso local foi aplicado, e uma caixa laranja geralmente indica que uma associação de dados foi aplicada. Quando você clica no marcador da propriedade, pode navegar para a definição de um estilo, abrir o construtor da associação de dados ou abrir o selecionador de recurso.  
  
## Consulte também  
 [Trabalhando com elementos no Designer XAML](../designers/working-with-elements-in-xaml-designer.md)   
 [Como criar e aplicar um recurso](../designers/how-to-create-and-apply-a-resource.md)   
 [Passo a passo: Associando dados no XAML Designer](../designers/walkthrough-binding-to-data-in-xaml-designer.md)