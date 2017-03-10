---
title: "Trabalhando com elementos no Designer XAML | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Trabalhando com elementos no Designer XAML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode adicionar elementos, controles, layouts e formas — para seu aplicativo no XAML, no código, ou usando o Designer XAML.  Este tópico descreve como trabalhar com elementos no Designer XAML no Visual Studio ou Blend para Visual Studio.  
  
## Adicionando um elemento a um layout  
 *Layout* é o processo de redimensionar e posicionar elementos em uma interface do usuário.  Para posicionar elementos visuais, você deve colocá\-los em um layout de [painel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx).  Um  `Panel` tem uma propriedade child que é uma coleção de [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx) tipos.  Você pode usar vários  `Panel` elementos filho, como [tela](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx), e [grade](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), para servir como contêineres de layout e para posicionar e organizar os elementos em uma página.  
  
 Por padrão, um `Grid` painel é usado como o contêiner de layout de nível superior dentro de uma página ou formulário.  Você pode adicionar painéis de layout, controles ou outros elementos dentro do layout de página de nível superior.  
  
#### Para adicionar um elemento a um layout  
  
-   No Designer XAML, siga um destes procedimentos:  
  
    -   Clique duas vezes em um elemento de **Toolbox** \(ou selecione um elemento na caixa de ferramentas e pressione Enter\).  
  
    -   Arraste um elemento do **Toolbox** à prancheta.  
  
    -   No **Toolbox**, selecione uma das ferramentas de desenho \(por exemplo, [Elipse](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) ou [retângulo](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)\) e, em seguida, desenhe um elemento no painel ativo.  
  
## Alterar a ordem das camadas de elementos  
 Quando há dois elementos na prancheta no Designer XAML, um elemento será exibido na frente do outro na ordem de camadas.  Na parte inferior da lista de elementos na estrutura de tópicos de documento janela é o elemento mais à frente \(exceto quando o **ZIndex** é definida para um elemento\).  Quando você insere um elemento em uma página, um formulário ou um contêiner de layout, o elemento é automaticamente colocado na frente de outros elementos no elemento de contêiner ativo.  Para alterar a ordem dos elementos, você pode usar o **ordem** comandos ou arrastar os elementos na árvore de objetos na janela estrutura de tópicos do documento.  
  
#### Para alterar a ordem das camadas  
  
-   Siga um destes procedimentos:  
  
    -   No **Document Outline** janela, arraste os elementos para cima ou para baixo para criar a ordem das camadas desejada.  
  
    -   Com o botão direito do elemento na janela estrutura de tópicos do documento ou na prancheta para a qual você deseja alterar a ordem das camadas, aponte para **ordem**, e, em seguida, clique em um dos seguintes:  
  
        -   **Trazer para frente** para colocar o elemento para a frente da ordem.  
  
        -   **Bring Forward** para colocar o elemento encaminhar um nível na ordem.  
  
        -   **Recuar** para enviar o elemento um nível na ordem.  
  
        -   **Enviar para trás** para enviar o elemento para trás da ordem.  
  
     Alterar o **ZIndex** propriedade o **Layout** seção na janela Propriedades.  Para sobrepor elementos, o **ZIndex** propriedade tem precedência sobre a ordem dos elementos exibidos na janela estrutura de tópicos do documento.  Um elemento que tem menos **ZIndex** valor é exibido na frente quando houver sobreposição de elementos.  
  
## Alterar o alinhamento de um elemento  
 Você pode alinhar elementos na prancheta usando comandos de menu ou arrastando elementos para guias de alinhamento.  
  
 Um *snapline* é uma indicação visual que ajuda a alinhar um elemento em relação a outros elementos no aplicativo.  
  
#### Para alinhar dois ou mais elementos usando comandos de menu  
  
1.  Selecione os elementos que você deseja alinhar.  Você pode selecionar mais de um elemento pressionando e mantendo pressionada a tecla Ctrl enquanto seleciona os elementos.  
  
2.  Selecione uma das seguintes propriedades em **HorizontalAlignment** no **Layout** seção da janela Propriedades: **esquerda**, **Center**, **direita**, ou **Stretch**.  
  
3.  Selecione uma das seguintes propriedades em **VerticalAlignment** no **Layout** seção da janela Propriedades: **superior**, **Center**, **inferior**, ou **Stretch**.  
  
#### Para alinhar dois ou mais elementos usando guias de alinhamento  
  
-   No Designer XAML, em um layout que contém pelo menos dois elementos, arraste ou redimensione um dos elementos de forma que a borda seja alinhada a outro elemento.  
  
     Quando as bordas estão alinhadas, um *limite de alinhamento* é exibida para indicar o alinhamento.  O limite de alinhamento é uma linha vermelha tracejada.  Limites de alinhamento só aparecem quando **ajuste às guias de alinhamento** está habilitado.  Para obter uma ilustração da prancheta que mostra um limite de alinhamento, consulte [Criando uma interface de usuário usando o Designer XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
## Alterar as margens de um elemento  
 As margens no XAML Designer determinam a quantidade de espaço vazio ao redor de um elemento na prancheta.  Por exemplo, as margens especificam a quantidade de espaço entre as bordas externas de um elemento e os limites de um  `Grid` painel que contém o elemento.  As margens também especificam a quantidade de espaço entre os elementos que estão contidos em um `StackPanel`.  
  
#### Para alterar as margens de um elemento na janela Propriedades  
  
1.  Selecione o elemento cujas margens você deseja alterar.  
  
2.  Em **Layout** na janela Propriedades, altere o valor \(em pixels ou unidades independentes de dispositivo, aproximadamente 1\/96 polegada\) para qualquer um do **margem** propriedades \(**superior**, **esquerda**, **direita**, ou **inferior**\).  
  
#### Para alterar as margens de um elemento na prancheta  
  
-   Para alterar as margens de um elemento em relação ao respectivo contêiner de layout, clique o *adornos de margem* que aparecem em torno do elemento na prancheta quando o elemento é selecionado e estiver em um contêiner de layout.  Para obter uma ilustração que mostra os adornos de margem, consulte [Criando uma interface de usuário usando o Designer XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     Se um adorno de margem estiver aberto, vertical ou horizontalmente, essa margem não está definida.  Se um adorno de margem estiver fechado, essa margem será definida.  
  
     Quando você abre um adorno de margem e a margem oposta não está definida, a margem oposta é definida como o valor correto de acordo com o local do elemento na prancheta.  Para margens opostas, como o **esquerda** e **direita** margens, pelo menos uma propriedade é sempre definida.  
  
    > [!IMPORTANT]
    >  Elementos colocados dentro de alguns contêineres de layout, como um <xref:Windows.UI.Xaml.Controls.Canvas>, não têm adornos de margem.  Elementos colocados dentro de um <xref:Windows.UI.Xaml.Controls.StackPanel> têm adornos para a esquerda e direita as margens ou as margens superior e inferior, dependendo da orientação do `StackPanel`.  
  
## Agrupando e desagrupando elementos  
 Agrupar dois ou mais elementos no Designer XAML cria um novo contêiner de layout e coloca esses elementos dentro do contêiner.  Colocação de dois ou mais elementos juntos em um contêiner de layout permite que você facilmente selecionar, mover e transformar o grupo como se os elementos nesse grupo fossem um único elemento.  O agrupamento também é útil para identificar elementos relacionados entre si de alguma forma, como os botões que compõem um elemento de navegação.  Ao desagrupar elementos, você simplesmente exclui o contêiner de layout que continha os elementos.  
  
#### Para agrupar elementos em um novo contêiner de layout  
  
1.  Selecione os elementos que você deseja agrupar.  \(Para selecionar vários elementos, pressione e segure a tecla Ctrl enquanto você clica neles\).  
  
2.  Clique com botão direito elementos selecionados, aponte para **agrupar em**, e, em seguida, clique no tipo de contêiner de layout no qual você deseja que o grupo resida.  
  
    > [!TIP]
    >  Se você selecionar <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, ou <xref:Windows.UI.Xaml.Controls.ScrollViewer> para agrupar seus elementos, os elementos são colocados em um novo <xref:Windows.UI.Xaml.Controls.Grid> dentro do painel de <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, ou <xref:Windows.UI.Xaml.Controls.ScrollViewer>.  Se você desagrupar elementos em um desses contêineres de layout, apenas o <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border>, ou <xref:Windows.UI.Xaml.Controls.ScrollViewer> é excluído e o <xref:Windows.UI.Xaml.Controls.Grid> painel permanece.  Para excluir o `Grid` painel, desagrupe os elementos novamente.  
  
#### Para desagrupar elementos e excluir o layout  
  
-   Com o botão direito do grupo que você deseja desagrupar e clique em **Desagrupar**.  
  
 Você também pode agrupar ou desagrupar elementos clicando com o botão itens selecionados na janela estrutura de tópicos do documento e clicando em **agrupar em** ou **Desagrupar**.  
  
## Redefinir o layout do elemento  
 Você pode restaurar valores padrão de propriedades de layout específicas de um elemento usando os comandos de redefinição do Layout.  Ao usar esse comando, você pode redefinir a margem, o alinhamento, a largura, a altura e o tamanho de um elemento individual ou coletivamente.  
  
#### Para redefinir o layout do elemento  
  
-   Na janela estrutura de tópicos do documento ou na prancheta, clique com botão direito do elemento, escolha **Layout**, **Redefinir** *PropertyName*, onde *PropertyName* é a propriedade que você deseja redefinir \(ou escolha **Layout**, **Redefinir tudo** para redefinir todas as propriedades de layout para o elemento\).  
  
## Consulte também  
 [Criando uma interface de usuário usando o Designer XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)