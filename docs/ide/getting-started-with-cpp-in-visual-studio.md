---
title: "Introdução à linguagem C++ no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 18
author: kempb
ms.author: kempb
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 65b94b58da1e06febb1c189ddff85f792fef1737
ms.contentlocale: pt-br
ms.lasthandoff: 05/13/2017

---
# <a name="getting-started-with-c-in-visual-studio"></a>Introdução à linguagem C++ no Visual Studio
Ao concluir esta explicação passo a passo, você estará familiarizado com várias ferramentas e caixas de diálogo que poderá usar ao desenvolver aplicativos com o Visual Studio. Você criará um aplicativo simples no estilo "Olá, Mundo" enquanto aprende mais sobre o trabalho no IDE (ambiente de desenvolvimento integrado).  
  
 Esse tópico contém as seguintes seções:  
  
 [Entrar no Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)  
  
 [Criar um aplicativo simples](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)  
  
 [Adicionar código ao aplicativo](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)  
  
 [Depurar e testar o aplicativo](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)  
  
 [Criar uma versão de lançamento do aplicativo](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)  
  
##  <a name="BKMK_Configure"></a> Entrar no Visual Studio  
 Quando você iniciar o Visual Studio pela primeira vez, terá a chance de entrar usando uma conta da Microsoft, como do Live ou do Outlook. Entrar permite que suas configurações sejam sincronizadas em todos os seus dispositivos. Para obter mais informações, consulte [Entrando no Visual Studio](../ide/signing-in-to-visual-studio.md)  
  
 Figura 1: IDE do Visual Studio  
  
 ![IDE com as configurações do Visual C&#43;&#43; aplicadas](~/ide/media/c--ide_defaultenvironmentlayout.png "C++IDE_DefaultEnvironmentLayout")  
  
 Depois de abrir o Visual Studio, você poderá ver as três partes básicas do IDE: janelas de ferramenta, menus e barras de ferramentas e o espaço da janela principal. As janelas de ferramentas estão encaixadas nos lados esquerdo e direito da janela do aplicativo, com **Início Rápido**, a barra de menus e a barra de ferramentas padrão na parte superior. O centro da janela do aplicativo contem a **Página Inicial**. Quando você abre uma solução ou um projeto, editores e designers aparecem neste espaço. Ao desenvolver um aplicativo, você passará a maior parte do seu tempo nessa área central.  
  
##  <a name="BKMK_CreateApp"></a> Criar um aplicativo simples  
 Quando você cria um aplicativo no Visual Studio, primeiro cria um projeto e uma solução. Para este exemplo, você criará um aplicativo de console do Windows.  
  
#### <a name="to-create-a-console-app"></a>Para criar um aplicativo do console  
  
1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     ![Na barra de menus, escolha Arquivo, Novo, Projeto](~/ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")  
  
2.  Na categoria **Visual C++**, escolha o modelo **Aplicativo do Console Win32** e nomeie o projeto como `GreetingsConsoleApp`.  
  
     ![Modelo Aplicativo do Console Win32](~/ide/media/c--ide_newprojectdlg.png "C++IDE_NewProjectDlg")  
     A caixa de diálogo pode ter diferentes opções, dependendo do que você instalou. Se você não vir os modelos de projeto do Visual C++, precisará voltar para o instalador e instale uma carga de trabalho do C++.
  
3.  Quando o Assistente de Aplicativo Win32 aparecer, escolha o botão **Finalizar**.  
  
     ![Assistente de Aplicativo do Console Win32](~/ide/media/c--ide_win32consoleappwizard.png "C++IDE_Win32ConsoleAppWizard")  
  
 O projeto e a solução GreetingsConsoleApp, com os arquivos básicos para um aplicativo de console Win32, são criados e automaticamente carregados no **Gerenciador de Soluções**. O arquivo GreetingsConsoleApp.cpp é aberto no editor de códigos. Os seguintes itens aparecem no **Gerenciador de Soluções**:  
  
 Figura 4: Itens do projeto  
  
 ![Arquivos para a solução no Gerenciador de Soluções](~/ide/media/c--ide_solutioncontents.png "C++IDE_SolutionContents")  
  
##  <a name="BKMK_AddCode"></a> Adicionar código ao aplicativo  
 Em seguida, você adicionará código para exibir a palavra “Hello” na janela do console.  
  
#### <a name="to-display-hello-in-the-console-window"></a>Para exibir “Olá” na janela do console  
  
1.  No arquivo GreetingsConsoleApp.cpp, insira uma linha em branco antes da linha `return 0;` e então insira o código a seguir:  
  
    ```  
    cout << "Hello\n";  
    ```  
  
     Uma pequena linha vermelha aparecerá em `cout`. Uma mensagem de erro aparecerá se você apontar para ele.  
  
     ![Texto de erro para cout](~/ide/media/c--ide_couterror.png "C++IDE_CoutError")  
  
     A mensagem de erro também aparece na janela **Lista de Erros**. Você pode exibir a janela escolhendo **Exibir**, **Lista de Erros** na barra de menus.  
  
     [cout](/cpp/standard-library/iostream) está incluído no arquivo de cabeçalho \<iostream>.  
  
2.  Para incluir o cabeçalho iostream, digite o seguinte código após `#include "stdafx.h"`:  
  
    ```  
    #include <iostream>  
    using namespace std;  
    ```  
  
     Você provavelmente observou que apareceu uma caixa quando o código foi inserido, fornecendo sugestões para os caracteres inseridos. Essa caixa é parte do IntelliSense do C++, que fornece prompts de codificação, incluindo a listagem de classes ou membros da interface e informações de parâmetro. Você também pode usar trechos de código, que são blocos de código predefinidos. Para obter mais informações, consulte [Usando IntelliSense](../ide/using-intellisense.md) e [Trechos de código](../ide/code-snippets.md).  
  
     A pequena linha vermelha em `cout` desaparecerá quando você corrigir o erro.  
  
3.  Salve as alterações no arquivo.  
  
     ![Código que corrige o erro de cout](~/ide/media/c--ide_coutfix.png "C++IDE_CoutFix")  
  
##  <a name="BKMK_DebugTest"></a> Depurar e testar o aplicativo  
 Você pode depurar o GreetingsConsoleApp para ver se a palavra "Hello" aparece na janela do console.  
  
#### <a name="to-debug-the-application"></a>Para depurar o aplicativo  
  
-   Inicie o depurador.  
  
     ![Comando Iniciar Depuração no menu Depurar](~/ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")  
  
     O depurador inicia e executa o código. A janela de console (uma janela separada que se parece com um prompt de comando) é exibida por alguns segundos mas fecha rapidamente quando o depurador interrompe a execução. Para ver o texto, você precisa definir um ponto de interrupção para interromper a execução do programa.  
  
#### <a name="to-add-a-breakpoint"></a>Para adicionar um ponto de interrupção  
  
1.  Adicione um ponto de interrupção da barra de menus na linha `return 0;`. Você também pode clicar na margem esquerda para definir um ponto de interrupção.  
  
     ![Comando Ativar/Desativar Pontos de Interrupção no menu Depurar](~/ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")  
  
     Um círculo vermelho aparece ao lado da linha de código na margem da extrema esquerda da janela do editor.  
  
2.  Pressione a tecla F5 para iniciar a depuração.  
  
     O depurador é iniciado e uma janela de console aparece mostrando a palavra **Hello**.  
  
     ![Texto Hello na janela Prompt de Comando do Windows](~/ide/media/c--ide_hellocommandwindow.png "C++IDE_HelloCommandWindow")  
  
3.  Pressione SHIFT + F5 para parar a depuração.  
  
 Para obter mais informações, consulte [Projetos de console](../debugger/debugging-preparation-console-projects.md).  
  
##  <a name="BKMK_BuildRelease"></a> Criar uma versão de lançamento do aplicativo  
 Agora que você verificou que tudo está funcionando, já pode preparar um build de versão do aplicativo.  
  
#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Para limpar os arquivos de solução e criar uma versão de lançamento  
  
1.  Da barra de menus, exclua os arquivos intermediários e os arquivos de saída criados durante compilações anteriores.  
  
     ![O comando Limpar Solução no menu Compilar](~/ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")  
  
2.  Altere a configuração de build para GreetingsConsoleApp de **Depuração** para **Versão**.  
  
     ![Criar uma versão de lançamento do aplicativo](~/ide/media/c--ide_changingbuildtorelease.png "C++IDE_ChangingBuildtoRelease")  
  
3.  Compile a solução.  
  
     ![Comando Compilar Solução no menu Compilar](~/ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
 Parabéns por concluir este passo a passo! Se desejar explorar mais exemplos, consulte [Amostras do Visual Studio](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>Consulte também  
 [Usando o IDE do Visual Studio para desenvolvimento de área de trabalho do C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)   
 [Passo a passo: criar um aplicativo simples com o Visual C# ou o Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)   
 [Dicas de produtividade para o Visual Studio](../ide/productivity-tips-for-visual-studio.md)   
 [Exemplos do Visual Studio](../ide/visual-studio-samples.md)   
 [Introdução ao desenvolvimento com o Visual Studio](../ide/get-started-developing-with-visual-studio.md)
