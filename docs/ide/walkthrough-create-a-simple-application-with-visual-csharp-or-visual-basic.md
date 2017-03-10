---
title: "Instru&#231;&#245;es passo a passo: criar um aplicativo simples com o Visual C# ou o Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: criar um aplicativo simples com o Visual C# ou o Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao concluir este passo a passo, você estará familiarizado com várias ferramentas, caixas de diálogo e designers que você pode usar ao desenvolver aplicativos com o Visual Studio. Você criará um simples "Hello, World"\-aplicação de estilo, projetar a interface do usuário, adicionar código e depurar erros enquanto você aprender mais sobre como trabalhar no ambiente de desenvolvimento integrado \(IDE\).  
  
 Este tópico contém as seguintes seções:  
  
 [Configurar o IDE](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)  
  
 [Criar um aplicativo simples](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)  
  
 [Depurar e testar o aplicativo](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)  
  
> [!NOTE]
>  Este passo a passo baseia\-se no Visual Studio Professional, que oferece o modelo de aplicativo do WPF no qual você criará o projeto para este passo a passo. Visual Studio Express para Windows Desktop também oferece o modelo, mas o Visual Studio Express para Windows e o Visual Studio Express para Web não. Para obter informações introdutórias sobre como usar o Visual Studio Express para Windows, consulte o [Developer Center para aplicativos da Windows Store](http://msdn.microsoft.com/windows/apps/br229519). Para obter informações introdutórias sobre como usar o Visual Studio Express para Web, consulte [Introdução ao ASP.NET](http://www.asp.net/get-started). Além disso, sua edição do Visual Studio e as configurações que você usa determinam os nomes e locais de alguns elementos da interface do usuário. Consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_ConfigureIDE"></a> Configurar o IDE  
 Quando você iniciar o Visual Studio pela primeira vez, o Visual Studio solicita que você entrar com uma conta de serviço de Microsoft \(MSA\), [entrar no Visual Studio](http://blogs.msdn.com/b/visualstudio/archive/2013/06/28/welcome-sign-in-to-visual-studio.aspx). Você não precisa entrar e pode fazer isso mais tarde.  
  
 Sobre o lançamento do Visual Studio, em seguida deve escolher uma combinação de configurações que aplica um conjunto de personalizações predefinidas ao IDE. Cada combinação de configurações foi projetada para facilitar o desenvolvimento de aplicativos.  
  
 Este passo a passo pressupõem que você aplicou **Configurações gerais de desenvolvimento**, que se aplica a menor quantidade de personalização ao IDE. Se você já tiver escolhido c\# ou Visual Basic \(ambas são boas opções\), você não precisa alterar suas configurações.  Se você quiser alterar as configurações, você pode usar o **Import and Export Settings Wizard**. Consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Depois de abrir o Visual Studio, você pode identificar as janelas de ferramentas, menus e barras de ferramentas e o espaço da janela principal. Janelas de ferramentas estão encaixadas nos lados esquerdo e direito da janela do aplicativo, com **início rápido**, barra de menus e barra de ferramentas padrão na parte superior. No centro da janela do aplicativo é o **Start Page**. Quando você carrega uma solução ou projeto, editores e designers aparecem no espaço onde o **Start Page** é. Ao desenvolver um aplicativo, você passará a maior parte de seu tempo nessa área central.  
  
 Figura 2: Visual Studio IDE  
  
 ![IDE com configurações gerais aplicadas](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE\-IDEwithgeneralsettings")  
  
 Você pode fazer personalizações adicionais no Visual Studio, como alterar a face da fonte e o tamanho do texto no editor ou o tema de cor do IDE, usando o **opções** caixa de diálogo. Dependendo da combinação de configurações que você aplicou, alguns itens na caixa de diálogo poderão não aparecer automaticamente. Você pode assegurar\-se de que todas as opções possíveis apareçam escolhendo o **Mostrar todas as configurações** caixa de seleção.  
  
 Figura 3: Caixa de diálogo de opções  
  
 ![Wirh de caixa de diálogo de opções Mostrar todas as opção de configurações](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE\-Optionsdialogbox")  
  
 Neste exemplo, você alterará o tema de cor do IDE de claro para escuro.  Você pode pular para criar um projeto se desejar.  
  
#### Para alterar o tema de cor do IDE  
  
1.  Abra o **opções** caixa de diálogo, escolhendo o **ferramentas** menu na parte superior e, em seguida, o **Opções...** item.  
  
     ![Comando Opções no menu Ferramentas](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE\-ToolsOptionsmenu")  
  
2.  Alterar o **tema da cor** para **escuro**, em seguida, clique em **OK**.  
  
     ![Tema de cor escura selecionado](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE\-Darkthemeoptionsdlgbox")  
  
 As cores no Visual Studio devem corresponder a imagem a seguir:  
  
 ![IDE com tema escuro](../ide/media/exploreide-darkthemeide.png "ExploreIDE\-DarkThemeIDE")  
  
 O tema de cor usado para imagens no restante deste passo a passo é o tema no claro. Para obter mais informações sobre como personalizar o IDE, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="BKMK_CreateApp"></a> Criar um aplicativo simples  
  
### Criar o projeto  
 Quando você cria um aplicativo no Visual Studio, você primeiro crie um projeto e uma solução. Para este exemplo, você criará um projeto do Windows Presentation Foundation \(WPF\).  
  
##### Para criar o projeto WPF  
  
1.  Crie um novo projeto. Na barra de menus, escolha **arquivo**, **novo**, **projeto...**.  
  
     ![Na barra de menus, escolha arquivo, novo, projeto](../ide/media/exploreide-filenewproject.png "ExploreIDE\-FileNewProject")  
  
     Você também pode digitar **novo projeto** no **início rápido** para fazer a mesma coisa.  
  
     ![Na caixa de ferramentas Inicialização rápida, especifique o novo projeto](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE\-QuickLaunchNewProjectsmall")  
  
2.  Escolha do Visual Basic ou o modelo de aplicativo do Visual c\# WPF escolhendo no painel esquerdo **instalados**, **modelos**, **Visual C\#**, **Windows**, por exemplo e, em seguida, escolhendo aplicativo WPF no painel central.  Nomeie o projeto HelloWPFApp na parte inferior da caixa de diálogo Novo projeto.  
  
     ![Criar um projeto do WPF em Visual Basic, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "ExploreIDE\-NewProjectVB")  
  
     OR  
  
     ![Crie um Visual C&#35; projeto, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE\-NewProjectcsharp")  
  
 O Visual Studio cria o projeto HelloWPFApp e a solução e o **Solution Explorer** mostra vários arquivos. O WPF Designer mostra um modo de exibição de design e um modo de exibição XAML de MainWindow. XAML em um modo de exibição de divisão. Você pode deslizar o divisor para mostrar mais ou menos de dois modos de exibição.  Você pode optar por ver apenas a exibição visual ou apenas o modo de exibição XAML. \(Para obter mais informações, consulte [WPF Designer para Windows Forms desenvolvedores](http://msdn.microsoft.com/pt-br/47ad0909-e89b-4996-b4ac-874d929f94ca)\). Os seguintes itens aparecem em **Solution Explorer**:  
  
 Figura 5: Itens de projeto  
  
 ![Solution Explorer com HelloWPFApp arquivos carregados](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE\-HelloWPFAppFiles")  
  
 Depois de criar o projeto, você pode personalizá\-lo. Usando o **propriedades** janela \(encontrado no **exibição** menu\), você pode exibir e alterar as opções de itens de projeto, controles e outros itens em um aplicativo. Usando as propriedades do projeto e páginas de propriedade, você pode exibir e alterar as opções de projetos e soluções.  
  
##### Para alterar o nome de MainWindow. XAML  
  
1.  O procedimento a seguir, você dará MainWindow um nome mais específico. Em **Solution Explorer**, selecione MainWindow. XAML. Você deve ver o **propriedades** janela, mas se você não fizer isso, escolha o **exibição** menu e o **janela propriedade** item. Alterar o **nome de arquivo** propriedade `Greetings.xaml`.  
  
     ![Janela de propriedades com nome de arquivo realçado](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE\-FilenameinPropertiesWindow")  
  
     **Solution Explorer** mostra que o nome do arquivo agora é Greetings. XAML e, se você expandir o nó de MainWindow. XAML \(por colocar o foco no nó e pressionando a tecla de seta para a direita\), você verá o nome MainWindow.xaml.vb ou MainWindow.xaml.cs agora é Greetings.xaml.vb ou Greetings.xaml.cs. Esse arquivo de código está aninhado sob o nó do arquivo. XAML para mostrar a que eles estão intimamente relacionados uns aos outros.  
  
    > [!WARNING]
    >  Essa alteração causa um erro que você aprenderá como depurar e corrigir em uma etapa posterior.  
  
2.  Em **Solution Explorer**, abra Greetings. XAML no modo de exibição Designer \(pressionando a tecla Enter enquanto o nó tem foco\) e selecione a barra de título da janela usando o mouse.  
  
3.  No **propriedades** janela, altere o valor da **título** propriedade `Greetings`.  
  
 A barra de título de MainWindow. XAML agora exibe saudações.  
  
### Projetar a interface do usuário \(UI\)  
 Adicionaremos três tipos de controles para este aplicativo: um controle TextBlock, dois controles RadioButton e um controle de botão.  
  
##### Para adicionar um controle TextBlock  
  
1.  Abra o **Toolbox** janela escolhendo o **exibição** menu e o **Toolbox** item.  
  
2.  No **Toolbox**, procure pelo controle TextBlock.  
  
     ![Caixa de ferramentas com o controle TextBlock realçado](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE\-TextBlockToolbox")  
  
3.  Adicione um controle TextBlock à superfície de design, escolhendo o item de TextBlock e arrastando\-o para a janela na superfície de design.  Centro de controle na parte superior da janela.  
  
 A janela deve se parecer com a ilustração a seguir:  
  
 Figura 7: Janela de saudações com controle TextBlock  
  
 ![Controle TextBlock no formulário saudações](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE\-GreetingswithTextblockonly")  
  
 A marcação XAML deve ser semelhante ao seguinte:  
  
```  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  
  
##### Para personalizar o texto no bloco de texto  
  
1.  No modo de exibição XAML, localize a marcação para TextBlock e altere o atributo de texto: `Text=”Select a message option and then choose the Display button.”`  
  
2.  Se o TextBlock não expandir para ajustar o modo de exibição de Design, aumente o controle TextBlock \(usando as captura alças nas bordas\) para que ele exiba todo o texto.  
  
3.  Salve suas alterações pressionando Ctrl\-s ou usando o **arquivo** item de menu.  
  
 Em seguida, você adicionará dois [RadioButton](../Topic/RadioButton.md) controles ao formulário.  
  
##### Para adicionar botões de opção  
  
1.  No **Toolbox**, procure pelo controle RadioButton.  
  
     ![Janela caixa de ferramentas com controle de botão de opção selecionado](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE\-RadioButtonToolbox")  
  
2.  Adicione dois controles RadioButton na estrutura de superfície, escolhendo o item RadioButton e arrastando\-a janela na superfície de design duas vezes e mover os botões \(selecionando\-as e usando as teclas de seta\) para que os botões são exibidos lado a lado sob o controle TextBlock.  
  
     A janela deve ter esta aparência:  
  
     Figura 8: RadioButtons na janela saudações.  
  
     ![Formulário de festas com textblock e dois botões de opção](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE\-Greetingswithradiobuttons")  
  
3.  No **propriedades** janela controle RadioButton esquerdo, altere o **nome** propriedade \(a propriedade na parte superior do **propriedades** janela\) para `RadioButton1`.  Verifique se que você selecionou o RadioButton e não o plano de fundo grade no formulário; o campo de tipo de janela de propriedade no campo nome deve dizer RadioButton.  
  
4.  No **propriedades** janela controle RadioButton direito, altere o **nome** propriedade `RadioButton2`, e, em seguida, salve as alterações pressionando Ctrl\-s ou usando o **arquivo** item de menu.  Verifique se que você selecionou o RadioButton antes de alterar e salvar.  
  
 Agora você pode adicionar texto de exibição para cada controle RadioButton. O procedimento a seguir atualiza o **conteúdo** propriedade de um controle RadioButton.  
  
##### Para adicionar texto de exibição para cada botão de opção  
  
1.  Na superfície de design, abra o menu de atalho de RadioButton1, pressionando o botão direito do mouse enquanto selecionando o RadioButton1, escolha **Editar texto**, e, em seguida, digite `Hello`.  
  
2.  Abra o menu de atalho de RadioButton2, pressionando o botão direito do mouse enquanto seleciona RadioButton2, escolha **Editar texto**, e, em seguida, digite `Goodbye`.  
  
 É o elemento de interface do usuário final que você adicionará um [botão](../Topic/Button.md) controle.  
  
##### Para adicionar o controle de botão  
  
1.  No **ferramentas**, procure o **botão** controle e, em seguida, adicioná\-lo à superfície de design em controles RadioButton selecionando o botão e arrastando\-o para o formulário no modo design.  
  
2.  No modo de exibição XAML, altere o valor de **conteúdo** para o controle de botão de `Content=”Button”` para `Content=”Display”`, e, em seguida, salve as alterações \(Ctrl\-s ou use o **arquivo** menu\).  
  
     A marcação deve se parecer com o exemplo a seguir: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  
  
 A janela deve se parecer com a ilustração a seguir.  
  
 Figura 9: Final de saudações da interface do usuário  
  
 ![Formulário de festas com rótulos de controle](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE\-Greetingswithconrollabels")  
  
### Adicione código ao botão Exibir  
 Quando esse aplicativo é executado, uma caixa de mensagem aparece depois que um usuário escolhe pela primeira vez um botão de opção e escolhe o **exibição** botão. Uma caixa de mensagem será exibida para Olá e outra aparecerá para adeus. Para criar esse comportamento, você adicionará código ao evento Button\_Click em Greetings.xaml.vb ou Greetings.xaml.cs.  
  
##### Adicione código para exibir caixas de mensagem  
  
1.  Na superfície de design, clique duas vezes o **exibição** botão.  
  
     Greetings.XAML.vb ou Greetings.xaml.cs é aberto, com o cursor no evento Button\_Click. Você também pode adicionar um manipulador de eventos da seguinte maneira \(se o código colado tiver um rabisco vermelho em quaisquer nomes, você provavelmente não selecionar os controles RadioButton na superfície de design e renomeá\-los\):  
  
     Para o Visual Basic, o manipulador de eventos deve ser assim:  
  
    ```vb#  
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)  
  
    End Sub  
    ```  
  
     Para o Visual c\#, o manipulador de eventos deve ser assim:  
  
    ```c#  
    private void Button_Click_1(object sender, RoutedEventArgs e)  
    {  
  
    }  
    ```  
  
2.  Para o Visual Basic, insira o código a seguir:  
  
    ```vb#  
    If RadioButton1.IsChecked = True Then  
        MessageBox.Show("Hello.")  
    Else RadioButton2.IsChecked = True  
        MessageBox.Show("Goodbye.")  
    End If  
  
    ```  
  
     Para o Visual c\#, digite o seguinte código:  
  
    ```  
    if (RadioButton1.IsChecked == true)  
    {  
        MessageBox.Show("Hello.");  
    }  
    else  
    {  
        RadioButton2.IsChecked = true;  
        MessageBox.Show("Goodbye.");  
    }  
    ```  
  
3.  Salve o aplicativo.  
  
##  <a name="BKMK_DebugTest"></a> Depurar e testar o aplicativo  
 Em seguida, você vai depurar o aplicativo para procurar erros e testar as duas caixas de mensagem são exibidas corretamente. As instruções a seguir descrevem como criar e iniciar o depurador, mas posteriormente você pode ler [Criando um aplicativo WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md) e [Depurando WPF](../debugger/debugging-wpf.md) para obter mais informações.  
  
### Localizar e corrigir erros  
 Nesta etapa, você encontrará o erro que nós causamos anteriormente alterando o nome da janela principal do arquivo XAML.  
  
##### Para iniciar a depuração e localizar o erro  
  
1.  Iniciar o depurador selecionando **Depurar**, em seguida, **Iniciar depuração**.  
  
     ![Comando de depuração iniciar no menu Debug](../ide/media/exploreide-startdebugging.png "ExploreIDE\-StartDebugging")  
  
     Uma caixa de diálogo é exibida, indicando que um IOException ocorreu: não é possível localizar o recurso 'MainWindow. xaml'.  
  
2.  Escolha o **OK** botão e, em seguida, pare o depurador.  
  
     ![Parar o comando de depuração no menu Debug](../ide/media/exploreide-stopdebugging.png "ExploreIDE\-StopDebugging")  
  
 Renomeamos MainWindow. XAML para Greetings. XAML no início deste passo a passo, mas o código ainda se refere a MainWindow. XAML como o URI de inicialização para o aplicativo, portanto não é possível iniciar o projeto.  
  
##### Para especificar Greetings. XAML como o URI de inicialização  
  
1.  Em **Solution Explorer**, abra o arquivo App. XAML \(no projeto do c\#\) ou o arquivo Application XAML \(no projeto do Visual Basic\) no modo de exibição XAML \(ele não pode ser aberto no modo de exibição Design\) selecioná\-lo e pressionando Enter ou clicando nele duas vezes.  
  
2.  Alterar `StartupUri="MainWindow.xaml"` para `StartupUri="Greetings.xaml"`, e, em seguida, salve as alterações com Ctrl\-s.  
  
 Inicie o depurador novamente \(pressione F5\). Você deve ver a janela saudações do aplicativo.  
  
### Para depurar com pontos de interrupção  
 Adicionando alguns pontos de interrupção, você pode testar o código durante a depuração. Você pode adicionar pontos de interrupção escolhendo **Depurar** no menu principal, em seguida, **Alternar ponto de interrupção** ou clicando na margem esquerda do editor ao lado da linha de código onde você deseja que a quebra ocorra.  
  
##### Para adicionar pontos de interrupção  
  
1.  Abra Greetings.xaml.vb ou Greetings.xaml.cs e selecione a linha a seguir: `MessageBox.Show("Hello.")`  
  
2.  Adicionar um ponto de interrupção no menu selecionando **Depurar**, em seguida, **Alternar ponto de interrupção**.  
  
     ![Ativar&#47;desativar ponto de interrupção comando no menu Debug](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE\-ToggleBreakpoint")  
  
     Um círculo vermelho aparece ao lado da linha de código na margem esquerda da janela do editor.  
  
3.  Selecione a linha a seguir: `MessageBox.Show("Goodbye.")`.  
  
4.  Pressione a tecla F9 para adicionar um ponto de interrupção e, em seguida, pressione a tecla F5 para iniciar a depuração.  
  
5.  No **saudações** janela, escolha o **Hello** botão de opção e, em seguida, escolha o **exibição** botão.  
  
     A linha `MessageBox.Show("Hello.")` é realçado em amarelo. Na parte inferior do IDE, Autos, locais e inspeção janelas são encaixadas no lado esquerdo e as janelas pilha de chamadas, pontos de interrupção, comando, imediato e saída são encaixadas no lado direito.  
  
6.  Na barra de menus, escolha **Depurar**, **Step Out**.  
  
     O aplicativo retoma a execução e é exibida uma caixa de mensagem com a palavra "Hello".  
  
7.  Escolha o **OK** botão na caixa de mensagem para fechá\-la.  
  
8.  No **saudações** janela, escolha o **adeus** botão de opção e, em seguida, escolha o **exibição** botão.  
  
     A linha `MessageBox.Show("Goodbye.")` é realçado em amarelo.  
  
9. Escolha a tecla F5 para continuar a depuração. Quando a caixa de mensagem for exibida, escolha o **OK** botão na caixa de mensagem para fechá\-la.  
  
10. Pressione SHIFT \+ F5 chaves \(pressione a tecla shift primeiro e mantendo\-o para baixo, pressione F5\) para parar a depuração.  
  
11. Na barra de menus, escolha **Depurar**, **Desabilitar todos os pontos de interrupção**.  
  
### Criar uma versão de lançamento do aplicativo  
 Agora que você verificou que tudo está funcionando, você pode preparar uma compilação de versão do aplicativo.  
  
##### Para limpar os arquivos de solução e criar uma versão de lançamento  
  
1.  No menu principal, selecione **criar**, em seguida, **Limpar solução** para excluir arquivos intermediários e arquivos de saída que foram criados durante compilações anteriores.  Isso não é necessário, mas ele limpa as saídas de compilação de depuração.  
  
     ![O comando Limpar solução no menu Build](../ide/media/exploreide-cleansolution.png "ExploreIDE\-CleanSolution")  
  
2.  Alterar a configuração de compilação de HelloWPFApp, de **Depurar** para **versão** usando o controle de lista suspensa na barra de ferramentas \(diz "Depuração" no momento\).  
  
     ![Barra de ferramentas padrão com a versão selecionada](../ide/media/exploreide-releaseversion.png "ExploreIDE\-ReleaseVersion")  
  
3.  Compile a solução escolhendo **criar**, em seguida, **Build Solution** ou pressione a tecla F6.  
  
     ![Comando de solução de compilação no menu Build](../ide/media/exploreide-buildsolution.png "ExploreIDE\-BuildSolution")  
  
 Parabéns por concluir este passo a passo\! Você pode encontrar o .exe criado no diretório do projeto e solução \(... \\HelloWPFApp\\HelloWPFApp\\bin\\Release\\\). Se você quiser explorar mais exemplos, consulte [Amostras do Visual Studio](../ide/visual-studio-samples.md).  
  
## Consulte também  
 [O que há de novo no Visual Studio 2015](../ide/what-s-new-in-visual-studio-2015.md)   
 [Guia de Introdução](../ide/get-started-developing-with-visual-studio.md)   
 [Dicas de produtividade](../ide/productivity-tips-for-visual-studio.md)