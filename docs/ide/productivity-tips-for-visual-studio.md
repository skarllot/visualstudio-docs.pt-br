---
title: Dicas de produtividade para o Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 28
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: cc0ac8b3418c725579b25712e14c373028fca339
ms.contentlocale: pt-br
ms.lasthandoff: 05/24/2017

---
# <a name="productivity-tips-for-visual-studio"></a>Dicas de produtividade para o Visual Studio
Seguindo estas dicas, você pode gravar, navegar e depurar seu código no Visual Studio com mais rapidez e eficiência. Para obter mais informações sobre atalhos de teclado comuns, veja [Dicas e Truques](../ide/tips-and-tricks-for-visual-studio.md). Para obter uma lista mais completa, consulte [Identificando e personalizando atalhos de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) e [Atalhos de teclado padrão](../ide/default-keyboard-shortcuts-in-visual-studio.md).  
  
 Este tópico inclui as seções a seguir:  
  
 [Acessando as Ferramentas do Visual Studio](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)  
  
 [Escrevendo código](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)  
  
 [Navegando em seu código](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)  
  
 [Localizando itens com mais rapidez](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)  
  
 [Depurando código](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)  
  
 [Gerenciando arquivos, barras de ferramentas e janelas](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)  
  
##  <a name="BKMK_Access"></a> Acessando as Ferramentas do Visual Studio  
 É possível acessar facilmente o Prompt de Comando do Desenvolvedor ou outra ferramenta se você fixá-la na Tela inicial ou na barra de tarefas.  
  
1.  Na tela inicial, digite `Visual Studio Tools` e, em seguida, pressione a tecla Enter.  
  
2.  No **Explorador de Arquivos**, abra o menu de atalho para o item que você deseja:  
  
    -   Notificações de Compilação  
  
    -   Gerenciador de pacotes depurável  
  
    -   Prompt de Comando do Desenvolvedor para VS2013  
  
    -   Microsoft Feedback Client 2013  
  
    -   Prompt de Comando de Ferramentas Cruzadas do VS2013 ARM  
  
    -   Prompt de Comando de Ferramentas Cruzadas do VS2013 x64  
  
    -   Prompt de Comando de Ferramentas Nativas do VS2013 x64  
  
    -   Prompt de Comando de Ferramentas Nativas do VS2013 x86  
  
3.  Escolha **Fixar em Iniciar** ou **Fixar na Barra de Tarefas**.  
  
##  <a name="BKMK_Writing"></a> Escrevendo código  
 Escreva código mais rapidamente usando os seguintes recursos.  
  
-   **Use aplicativos de exemplo**. Você pode acelerar o desenvolvimento de aplicativos ao baixar e instalar aplicativos de exemplo da Galeria de Códigos do MSDN. Você também pode aprender uma tecnologia em particular ou um conceito baixando e explorando um Sample Pack para essa área.  
  
-   **Use o IntelliSense**. À medida que você inserir código no editor, informações do IntelliSense, como Membros da Lista, Informações do Parâmetro, Informações Rápidas, Ajuda de Assinatura e Completar Palavras, serão exibidas. Esses recursos dão suporte à correspondência difusa de texto; por exemplo, as listas de resultados para Membros da Lista incluem não só entradas que começam com os caracteres que você inseriu, como também entradas que contêm a combinação de caracteres em qualquer lugar de seus nomes. Para obter mais informações, veja [Usando o IntelliSense](../ide/using-intellisense.md).  
  
-   **Altere a inserção automática de opções do IntelliSense à medida que você insere o código**. Ao alternar o IntelliSense para o modo de sugestão, você pode especificar que opções do IntelliSense será inseridas somente se você as escolher explicitamente.  
  
     Para habilitar o modo de sugestão, escolha de teclas CTRL + Alt + Barra de espaços ou, na barra de menus, escolha **Editar**, **IntelliSense**, **Ativar/Desativar Modo de Preenchimento**.  
  
-   **Use trechos de código**. Você pode usar snippets internos ou criar seus próprios snippets.  
  
     Para inserir um trecho, na barra de menus, escolha **Editar**, **IntelliSense**, **Inserir Trecho** ou abra o menu de atalho em um arquivo e escolha **Inserir Trecho**. Para obter mais informações, consulte [Trechos de Código](../ide/code-snippets.md).  
  
-   **Corrija erros de código embutidos**. Marcas inteligentes aparecem como caixas azuis ou vermelhas sob uma linha de código. Você pode exibir opções de marcas inteligentes apontando para uma das caixas ou colando o cursor na linha de código e escolhendo as teclas Ctrl +. (ponto).  
  
     As caixas azul sugerem maneiras de corrigir erros em seu código.  
  
     Figure 1: Marcas Inteligentes de erro  
  
     ![Sugestões de marcação inteligente de erro](../ide/media/productivity_bluesmarttags.png "Productivity_BlueSmartTags")  
  
     As caixas vermelhas sugerem maneiras de refatorar seu código.  
  
     Figure 2: Refatorando Marcas Inteligentes  
  
     ![Sugestões de marcação inteligente de refatoração](../ide/media/productivity_redsmarttags.png "Productivity_RedSmartTags")  
  
-   **Exibir e editar a definição de um elemento de código**. Você pode exibir e editar rapidamente o módulo no qual um elemento de código, como um membro, uma variável ou um local, é definido.  
  
     Para abrir uma definição em uma janela pop-up, realce o elemento e escolha as chaves Alt+F12 ou abra o menu de atalho do elemento e escolha **Inspecionar Definição**. Para abrir uma definição em uma janela de código separada, abra o menu de atalho para o elemento de código e então escolha **Ir Para Definição**.  
  
##  <a name="BKMK_Navigating"></a> Navegando em seu código  
 Você pode usar várias técnicas para localizar e mover para locais específicos em seu código com mais rapidez.  
  
-   **Usar indicadores em linhas de código**. Você pode usar indicadores para navegar rapidamente para linhas específicas do código em um arquivo.  
  
     Para definir um indicador, na barra de menus, escolha **Editar**, **Indicadores**, **Ativar/Desativar Indicador**. Você pode exibir todos os indicadores para uma solução na janela **Indicadores**. Para obter mais informações, consulte [Definindo Indicadores no Código](../ide/setting-bookmarks-in-code.md).  
  
-   **Pesquisar definições de símbolo em um arquivo**. Você pode pesquisar em uma solução para localizar definições de símbolos e nomes de arquivos, mas os resultados da pesquisa não incluirão os namespaces ou as variáveis locais.  
  
     Para acessar esse recurso, na barra de menus, escolha **Editar**, **Navegar Até**.  
  
-   **Procure a estrutura geral do seu código**. No **Gerenciador de Soluções**, você pode pesquisar e procurar classes e seus tipos e membros em seus projetos. Você também pode pesquisar símbolos, exibir a Hierarquia de Chamada de um método, localizar referências de símbolos e realizar outras tarefas. Se você escolher um elemento de código no **Gerenciador de Soluções**, o arquivo associado será aberto em uma guia **Visualização** e o cursor se moverá para o elemento no arquivo. Para obter mais informações, consulte [Exibindo a estrutura do código](../ide/viewing-the-structure-of-code.md).  
  
##  <a name="BKMK_Finding"></a> Localizando itens com mais rapidez  
 Você pode procurar no IDE comandos, arquivos e opções, bem como filtrar o conteúdo de janelas de ferramenta para mostrar somente as informações relevantes para sua tarefa atual.  
  
-   **Filtrar o conteúdo de janelas de ferramentas**. Você pode pesquisar no conteúdo de muitas janelas de ferramentas, como a **Caixa de Ferramentas**, a janela **Propriedades** e o **Gerenciador de Soluções**, mas só poderá exibir itens cujos nomes contenhamos caracteres que você especificar.  
  
-   **Exiba apenas os erros que você deseja resolver**. Se você escolher o botão **Filtrar** na barra de ferramentas **Lista de Erros**, poderá reduzir o número de erros que aparecem na janela **Lista de Erros**. Você só pode exibir os erros em arquivos que estão abertos no editor, somente os erros no arquivo atual ou somente os erros no projeto atual. Você também pode pesquisar na janela Lista de Erros para localizar erros específicos.  
  
-   **Localizar caixas de diálogo, comandos de menu e opções**. Na [Caixa de diálogo de início rápido, ambiente, opções](../ide/reference/quick-launch-environment-options-dialog-box.md), digite palavras-chave ou frases sobre os itens que você está tentando localizar. Por exemplo, as seguintes opções aparecerão se você inserir `new project`:  
  
     Figura 3: lista de resultados do Início Rápido para `new project`  
  
     ![Resultados de Início Rápido para 'novo projeto'](../ide/media/productivity_quicklaunch.png "Productivity_QuickLaunch")  
  
     O **Início Rápido** exibe links para a caixa de diálogo de **Novo Projeto**, a caixa de diálogo **Adicionar Novo Item** e a página Projetos e Soluções na caixa de diálogo **Opções**, entre outros. Os resultados do Início Rápido também podem incluir arquivos de projeto e janelas de ferramenta.  
  
##  <a name="BKMK_Debugging"></a> Depurando código  
 A depuração pode consumir muito tempo, mas as dicas a seguir podem ajudar a acelerar o processo.  
  
-   **Teste a mesma página, aplicativo ou site em navegadores diferentes**. À medida que você depura seu código, poderá facilmente mudar entre os navegadores da Web instalados, incluindo o [Inspetor de Página (Visual Studio)](http://msdn.microsoft.com/Library/65880969-1ad2-47be-85b9-bb12c81bf209), sem ter que abrir a caixa de diálogo **Procurar Com**. Você pode usar a lista **Destino de Depuração**, que está na barra de ferramentas **Standard** ao lado do botão **Iniciar Depuração**, para verificar rapidamente qual navegador está utilizando enquanto depura ou exibe as páginas.  
  
     ![Selecionar as opções de depuração do navegador da Web](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")  
  
-   **Definir pontos de interrupção temporários**. Você pode criar um ponto de interrupção temporário na linha de código atual e iniciar o depurador simultaneamente. Quando você atinge esta linha de código, o depurador entra em modo de interrupção. Para obter mais informações, veja [Navegação pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md).  
  
     Para usar este recurso, escolha de teclas CTRL + F10 ou abra o menu de atalho para a próxima linha de código em que você deseja quebrar e, então, escolha **Executar até o Cursor**.  
  
-   **Mover o ponto de execução durante a depuração**. Você pode mover o ponto de execução atual para uma seção de código diferente e então reiniciar a depuração desse ponto. Essa técnica será útil se você quiser depurar uma seção de código sem precisar recriar todas as etapas necessárias para acessar a seção. Para obter mais informações, veja [Navegação pelo código com o depurador](../debugger/navigating-through-code-with-the-debugger.md).  
  
     Para mover o ponto de execução, arraste a seta amarela para uma localidade onde deseja definir a declaração seguinte no mesmo arquivo de origem e então escolha a tecla F5 para continuar a depuração.  
  
-   **Capturar informações de valor de variáveis**. Você pode adicionar um DataTip a uma variável no seu código e fixá-lo para poder acessar o último valor conhecido da variável após a conclusão da depuração. Para obter mais informações, consulte [Exibir valores de dados em Dicas de Dados](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).  
  
     Para adicionar um DataTip, o depurador deverá estar em modo de interrupção. Coloque o cursor na variável e então escolha o botão de fixação no DataTip em que ele aparece. Quando a depuração é interrompida, um ícone de pino azul aparece no arquivo de origem ao lado da linha de código que contém a variável. Se você apontar para o pino azul, será exibido o valor da variável de sessão de depuração mais recente.  
  
-   **Limpar a janela Imediata**. Você pode apagar rapidamente os conteúdos da [Janela Imediata](../ide/reference/immediate-window.md) em tempo de design inserindo `>cls` ou `>Edit.ClearAll`  
  
     Para obter mais informações sobre comandos adicionais, consulte [Aliases de comando do Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
##  <a name="BKMK_Managing"></a> Gerenciando arquivos, barras de ferramentas e janelas  
 A qualquer momento, você pode estar trabalhando em vários arquivos de código e se mover entre várias janelas de ferramenta enquanto desenvolve um aplicativo. Você pode se manter organizado usando as dicas a seguir.  
  
-   **Manter arquivos que você usa frequentemente visíveis no editor**. Você pode fixar arquivos no lado esquerdo da guia de forma que eles permaneçam visíveis, independentemente de quantos arquivos estiverem abertos no editor.  
  
     Para fixar um arquivo, escolha a guia do arquivo e, então, selecione o botão **Ativar/desativar status de pin**.  
  
-   **Mover documentos e janelas para outros monitores**. Se você usar mais de um monitor quando desenvolver aplicativos, poderá trabalhar em partes do seu aplicativo mais facilmente movendo arquivos que estejam abertos no editor para outro monitor. Você também pode mover janelas de ferramentas, como as de depuração, para outro monitor e encaixar as janelas de documentos e de ferramentas para criar "rafts". Para obter mais informações, consulte [Personalização de layouts de janela no Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).  
  
     Você também pode gerenciar arquivos mais facilmente criando outra instância do **Gerenciador de Soluções** e movendo-a para outro monitor. Para criar outra instância do **Gerenciador de Soluções**, abra um menu de atalho no **Gerenciador de Soluções** e então escolha **Novo Modo de Exibição do Gerenciador de Soluções**.  
  
-   **Personalizar as fontes que aparecem no Visual Studio**. Você pode alterar o tipo de fonte, a cor e o tamanho usados para o texto no IDE. Por exemplo, você pode personalizar a cor de elementos de código específicos no editor e a fonte em janelas de ferramenta ou por meio do IDE. Para obter mais informações, consulte [Como alterar fontes e cores](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) e [Como alterar fontes e cores no Editor](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atalhos de teclado padrão para comandos frequentes](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)   
 [Como personalizar menus e barras de ferramentas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)   
 [Passo a passo: criar um aplicativo simples](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)   
 [Dicas e truques de acessibilidade](../ide/reference/accessibility-tips-and-tricks.md)
