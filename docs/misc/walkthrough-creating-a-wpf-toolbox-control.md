---
title: "Passo a passo: Criando um controle de caixa de ferramentas do WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "caixa de ferramentas"
  - "WPF"
ms.assetid: 8223c06e-f327-4778-8709-e0cc7eae2c78
caps.latest.revision: 15
caps.handback.revision: 15
manager: "douge"
---
# Passo a passo: Criando um controle de caixa de ferramentas do WPF
O modelo de controle de caixa de ferramentas do WPF que está incluído no SDK do Visual Studio permite que você crie controles do Windows Presentation Foundation \(WPF\) que são adicionados automaticamente para o **Toolbox** quando a extensão é instalada. Este passo a passo mostra como usar o modelo para criar um controle de contador que você pode distribuir para outros usuários.  
  
## Pré-requisitos  
 Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Localizando o modelo de controle de caixa de ferramentas do WPF no Visual Studio  
 O modelo de controle de caixa de ferramentas do WPF está disponível na **novo projeto** caixa de diálogo **modelos instalados**, nos seguintes locais:  
  
-   **Visual Basic**, **extensibilidade**. O idioma do projeto é o Visual Basic.  
  
-   **Visual C\#**, **extensibilidade**. O idioma do projeto é c\#.  
  
## Criando um projeto de controle de caixa de ferramentas do WPF  
 O modelo de controle de caixa de ferramentas do WPF cria um controle de usuário indefinido e fornece toda a funcionalidade necessária para adicionar o controle para o **Toolbox**.  
  
#### Para criar o projeto  
  
1.  Sobre o **arquivo** menu, clique em **novo**, e, em seguida, clique em **projeto**.  
  
2.  No **novo projeto** caixa de diálogo **modelos instalados**, clique no nó para sua linguagem de programação preferencial e, em seguida, selecione **extensibilidade**. Na lista de tipos de projeto, selecione **controle de caixa de ferramentas do WPF**.  
  
3.  No **nome** digite o nome que você deseja usar para o projeto. \(Este passo a passo usa o nome `Counter`.\) Clique em **OK**.  
  
     Isso cria uma solução que contém um controle de usuário, um atributo para colocar o controle no **Toolbox**, e um VSIX de manifesto de implantação. O **nome** caixa define o nome da solução e o nome do namespace, mas ele não define o nome do controle como ele aparece no **Toolbox**. Você irá definir que mais tarde no passo a passo.  
  
### Criando uma Interface de usuário para o controle  
 O `Counter` controle requer três controles filho: dois <xref:System.Windows.Controls.Label> controles para exibir o texto e a contagem atual e um <xref:System.Windows.Controls.Button> controle Redefinir a contagem como 0. Não há outros controles filho são necessários, pois hospedando aplicativos incrementará o contador de forma programática.  
  
##### Para criar a interface do usuário  
  
1.  Em **Solution Explorer**, clique duas vezes em ToolboxControl.cs para abri\-lo no designer.  
  
     O designer mostra um <xref:System.Windows.Controls.Grid> controle que contém um <xref:System.Windows.Controls.Button> controle.  
  
2.  Selecione o <xref:System.Windows.Controls.Grid> de controle e, em seguida, clique nas barras azuis que aparecem nos lados superior e esquerdos da grade para dividi\-la em duas linhas e duas colunas.  
  
3.  Do **Toolbox**, arraste um <xref:System.Windows.Controls.Label> controle para cada uma das células na linha superior da grade.  
  
     Neste ponto, você pode definir o layout do controle organizando os elementos na grade. Em vez disso, você pode editar o XAML Extensible Application Markup Language \(\) diretamente para que o controle será redimensionado dinamicamente para se ajustar ao texto.  
  
4.  No **XAML** painel, definir a altura do `RowDefinition` elementos e a largura do `ColumnDefinition` elementos `"auto"`.  
  
5.  Edite a marcação para o botão e dois rótulos para se parecer com o exemplo a seguir.  
  
     [!code-xml[ToolboxControlWPF#11](../misc/codesnippet/Xaml/walkthrough-creating-a-wpf-toolbox-control_1.xaml)]  
  
     O `Grid.Row` e `Grid.Column` atributos definir a posição dos elementos na grade. O `Grid.ColumnSpan` atributo no botão permite que a primeira coluna ser redimensionados independentemente da largura do botão.  
  
     O `Content` atributos da rótulos, use um `{Binding}` sintaxe para associar propriedades que você definirá posteriormente no passo a passo.  
  
### Codificar o controle de usuário  
 O `Counter` controle irá expor um método para incrementar o contador, de um evento a ser gerado sempre que o contador é incrementado, uma `Reset` botão e três propriedades para armazenar a contagem atual, o texto de exibição e se deseja mostrar ou ocultar o `Reset` botão. O `ProvideTolboxControl` atributo determina onde o **Toolbox** o `Counter` controle será exibido.  
  
 Você pode escrever esse controle da mesma maneira que você escreveria um controle de formulários do Windows, ou seja, usando manipuladores de eventos e métodos públicos para definir o conteúdo dos rótulos. No entanto, no WPF você pode definir um contexto de dados para o controle de forma que você pode associar atributos do elemento XAML diretamente a propriedades no código. Esse modelo também fornece uma camada de abstração para separar a funcionalidade básica da interface do usuário \(IU\) do controle.  
  
 Este passo a passo mostra como criar uma classe de modelo de dados e, em seguida, associar o contexto de dados do controle para o modelo de dados.  
  
##### Para criar um modelo de dados  
  
1.  Clique duas vezes no botão para abrir a janela de código.  
  
2.  Na parte superior do arquivo, adicione uma `using` diretriz para a <xref:System.ComponentModel> namespace.  
  
3.  Após a classe gerada, crie uma classe pública para definir o contexto de dados.  
  
     [!code-cs[ToolboxControlWPF#01](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_2.cs)]  
  
     Essa classe implementa o <xref:System.ComponentModel.INotifyPropertyChanged> interface, que permite que os elementos XAML ligar ao definir propriedades.  
  
4.  Clique com botão direito do <xref:System.ComponentModel.INotifyPropertyChanged> declaração de interface, clique em **implementar Interface**, e, em seguida, clique em **implementar Interface** novamente.  
  
     Visual Studio declara um `PropertyChanged` eventos.  
  
5.  Após a declaração de evento, crie o seguinte método privado para gerar o evento.  
  
     [!code-cs[ToolboxControlWPF#02](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_3.cs)]  
  
6.  Crie os seguintes campos particulares e propriedades públicas para manter os valores dos dois rótulos no controle.  
  
     [!code-cs[ToolboxControlWPF#03](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_4.cs)]  
  
     Gerando o `PropertyChanged` evento faz com que a ligação XAML atualizar o conteúdo dos controles associados. Definindo as propriedades como `public` torna disponíveis para os designers, mas não para outros programas, a menos que eles vinculam a esse contexto de dados.  
  
 Agora que você criou o modelo de dados, você pode implementar a funcionalidade de lógica do controle.  
  
##### Para implementar o controle  
  
1.  Na definição da classe parcial que implementa o controle, clique no nome de classe, clique em **Refatorar**, clique em **Renomear**, e, em seguida, altere o nome da classe para `Counter`. Esse é o nome que será exibido no **Toolbox** quando a extensão é instalada.  
  
2.  Imediatamente acima da definição de classe, no `ProvideToolboxControl` declaração do atributo, altere o valor do primeiro parâmetro de `"Counter"` para `"General"`. Isso define o nome do grupo de itens que hospedará o controle de **Toolbox**.  
  
     A exemplo a seguir mostra o `ProvideToolboxControl` atributo e a definição da classe ajustado.  
  
     [!code-cs[ToolboxControlWPF#04](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_5.cs)]  
  
3.  Criar um campo particular para manter o contexto de dados para o controle e, em seguida, no construtor, atribuir o contexto de dados para o `MyDataModel` de classe, conforme mostrado no exemplo a seguir.  
  
     [!code-cs[ToolboxControlWPF#05](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_6.cs)]  
  
4.  Crie as seguintes propriedades públicas para espelhar o `Text` e `Count` Propriedades de contexto de dados.  
  
     [!code-cs[ToolboxControlWPF#06](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_7.cs)]  
  
     Essas propriedades disponibilizar o conteúdo do contexto de dados para qualquer aplicativo que inclui o controle.  
  
5.  Crie o seguinte método público para incrementar o contador e um evento para notificar o aplicativo de hospedagem.  
  
     [!code-cs[ToolboxControlWPF#07](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_8.cs)]  
  
6.  Implementar o manipulador de cliques para o `Reset` botão da seguinte maneira.  
  
     [!code-cs[ToolboxControlWPF#08](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_9.cs)]  
  
7.  Adicione a seguinte propriedade pública para mostrar ou ocultar o `Reset` botão.  
  
     [!code-cs[ToolboxControlWPF#09](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_10.cs)]  
  
## Testando o controle  
 Para testar um **Toolbox** controlar, primeiro testá\-lo no ambiente de desenvolvimento e teste\-o em um aplicativo de hospedagem.  
  
#### Para testar o controle  
  
1.  Pressione F5.  
  
     Isso cria o projeto e abre uma segunda instância do Visual Studio que tem o controle instalado.  
  
2.  Na nova instância do Visual Studio, crie um projeto de aplicativo WPF.  
  
3.  Em **Solution Explorer**, clique duas vezes em MainWindow. XAML para abri\-lo no designer.  
  
4.  Do **geral** seção o **ferramentas**, arraste um **contador** controle ao seu formulário e, em seguida, selecioná\-lo.  
  
     O `Text` e `ShowReset` propriedades devem ser exibidas no **propriedades** janela, junto com outras propriedades herdadas do <xref:System.Windows.Controls.UserControl>. O `Count` propriedade não deve ser exibida porque é somente leitura.  
  
5.  Altere o valor de `Text` propriedade.  
  
     Deve alterar o texto do rótulo que é exibido no designer.  
  
6.  Definir o `ShowReset` propriedade `Hidden`, e defina\-o novamente para `Visible`.  
  
     O `Reset` botão no controle deve desaparecer e exibida novamente.  
  
7.  Arraste um <xref:System.Windows.Controls.Button> o controle para o formulário, defina sua `Content```atributo `Test`, e, em seguida, clique duas vezes no botão para abrir o manipulador de cliques na visualização de código.  
  
8.  Implementar o manipulador de cliques para chamar o `Increment` método do controle.  
  
     [!code-cs[ToolboxControlWPF#21](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_11.cs)]  
  
9. Na função de construtor, após a chamada para `InitializeComponent`, digite `counter1.Implemented +=`, e pressione a tecla TAB duas vezes para gerar um manipulador para o `Counter.Incremented` evento.  
  
10. Implemente o novo manipulador, conforme mostrado no exemplo a seguir.  
  
     [!code-cs[ToolboxControlWPF#22](../misc/codesnippet/CSharp/walkthrough-creating-a-wpf-toolbox-control_12.cs)]  
  
11. Pressione F5.  
  
     O aplicativo WPF deve abrir.  
  
12. Clique em **teste**.  
  
     Deve incrementar o contador e o botão deve desaparecer ligeiramente.  
  
13. Clique em **teste** mais quatro vezes.  
  
     Deve incrementar o contador e o botão deve continuar esmaecer até que ele desapareça. Se você continuar clicando em onde o botão estava, o contador deve continuar a incrementar.  
  
14. Clique em **Redefinir**.  
  
     O contador deve ser redefinido para **0**.  
  
## Próximas etapas  
 Quando você cria um **Toolbox** controle, o Visual Studio cria um arquivo chamado *ProjectName*. VSIX na pasta \\bin\\debug\\ do seu projeto. Você pode implantar o controle, carregando o arquivo. VSIX em uma rede ou para um site da Web. Quando um usuário abre o arquivo. VSIX, o controle seja instalado e adicionado ao Visual Studio **Toolbox**. Como alternativa, se você carregar o arquivo. VSIX para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) Web site para que os usuários possam encontrá\-lo navegando em **Extension Manager**.  
  
## Consulte também  
 [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md)   
 [Criando um controle de caixa de ferramentas do Windows Forms](../extensibility/creating-a-windows-forms-toolbox-control.md)   
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Trabalhando com controles no WPF Designer](http://msdn.microsoft.com/pt-br/c6235492-b10d-4c3c-ba67-6b6a545faee1)   
 [Visão geral sobre criação de controle](../Topic/Control%20Authoring%20Overview.md)