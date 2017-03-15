---
title: "Introdução ao Visual Studio | Microsoft Docs"
description: "Aprenda as noções básicas sobre como começar a usar o Visual Studio"
ms.custom: 
ms.date: 12/05/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, getting started
ms.assetid: 38e90339-1da5-410c-8ba4-437fc556cba7
caps.latest.revision: 65
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
translationtype: Human Translation
ms.sourcegitcommit: 27493b53229d9ceb6bc215fcf3d57a60fe4358b0
ms.openlocfilehash: 452f8dbd2c7eb4bcc2f0310da1f04c6dd031f629

---
# <a name="get-started-with-visual-studio"></a>Introdução ao Visual Studio

O Visual Studio é uma avançada ferramenta para desenvolver seus aplicativos. Vá em frente, baixe e instale o [Visual Studio](https://aka.ms/vs/15/preview/vs_enterprise) se você ainda não fez isso. Consulte o vídeo [Getting Started with Visual Studio – Setting up your IDE (Introdução ao Visual Studio – Configurando seu IDE)](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) para obter mais informações sobre como baixar o Visual Studio e configurá-lo da forma desejada.

## <a name="visual-studio-tour"></a>Tour pelo Visual Studio
O Visual Studio tem um grupo de janelas de ferramentas, menus e barras de ferramentas conhecidas coletivamente como o ambiente de desenvolvimento integrado ou IDE. O IDE do Visual Studio o ajuda a realizar suas tarefas de desenvolvimento. Aqui está uma visão geral de itens do IDE que você provavelmente usará com mais frequência.

### <a name="code-editor"></a>Editor de código
Uma das janelas de ferramentas mais usadas do Visual Studio. É aqui que você escreve e exibe seu código e navega por ele.

![Editor de Códigos](../ide/media/VSIDE_CodeWindow.png)

Quando você insere o código, o editor de código o ajuda a escrever e encontrar seu código mais facilmente fornecendo recursos como preenchimento de declaração, colorização de sintaxe, modo de mapa e muito mais. Para obter mais informações, assista ao vídeo [Getting Started with Visual Studio – Editing and navigating your code (Introdução ao Visual Studio – Editando e navegando em seu código)](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5)

Alguns tipos de solução podem incluir formulários, como WPF ou Windows Forms. Nesses casos, você também verá um designer visual neste espaço que lhe permite adicionar controles ao formulário visualmente, como botões e caixas de listagem.

### <a name="solution-explorer"></a>Gerenciador de Soluções

Uma janela de ferramentas chamada **Gerenciador de Soluções** lista todos os arquivos de código. O Gerenciador de Soluções pode ajudar a organizar seu código agrupando seus arquivos em projetos e soluções. O projeto em negrito é chamado de projeto de inicialização. É o primeiro código executado quando você inicia sua solução. É possível alterar o projeto de inicialização. Assista ao vídeo [Getting Started with Visual Studio – Building blocks of the IDE (Introdução ao Visual Studio – Criando blocos do IDE)](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) para obter mais informações.

![Nós recolhidos do Gerenciador de Soluções](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 Além de soluções e projetos, o Gerenciador de Soluções lista todos os arquivos em cada projeto quando você expande o nó do projeto. Cada projeto contém um ou mais arquivos, como arquivos de código-fonte e de recursos como imagens ou bibliotecas.

![Gerenciador de Soluções](../ide/media/VSIDE_SolutionExplorer3.png)

Para ver as propriedades de soluções, projetos e arquivos, escolha o comando **Propriedades** no menu de atalho (clique com botão direito do mouse) ou escolha **Exibir, janela Propriedades** no menu.

![Janela de Propriedades](../ide/media/VSIDE_SolutionExplorer4.png)

Não é necessário para criar uma solução ou projeto para começar a codificar. Você pode simplesmente começar de uma vez e abrir arquivos de código no Visual Studio, como arquivos clonados de um repositório Git e começar a editá-los imediatamente. Os arquivos serão exibidos no Gerenciador de Soluções e terão colorização de sintaxe, preenchimento de declaração básico e muito mais, assim como soluções tradicionais. Consulte [Abrir qualquer pasta](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) para obter mais informações.

### <a name="toolbar-and-menus"></a>Barra de ferramentas e menus
Para executar seu projeto, criar novas soluções, salvar arquivos e mais, use os comandos de barra de ferramentas e de menu do Visual Studio. Por exemplo, quando seu código estiver pronto para depurar, será possível escolher o botão **Iniciar** na barra de ferramentas ou escolher **Depurar, Iniciar depuração** no menu. Para criar uma nova solução, escolha o botão **Novo Projeto** ou escolha **Arquivo, Novo, Projeto** no menu e assim por diante.

![Barra de ferramentas do Visual Studio](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

Observe que esses ícones da barra de ferramentas e comandos de menu podem mudar dependendo do contexto, que significa o item selecionado no momento.

### <a name="team-explorer"></a>Team Explorer
O **Team Explorer** permite que você se conecte a ferramentas de controle do código-fonte como [Git](https://git-scm.com/) e [TFVC (Controle de Versão do Team Foundation)](https://www.visualstudio.com/en-us/docs/tfvc/overview) para armazenar seu código localmente ou compartilhá-lo com outras pessoas em um serviço hospedado. Também é possível usá-lo para rastrear tarefas e mais.

Assista aos vídeos [Getting Started with Visual Studio – Building blocks of the IDE (Introdução ao Visual Studio – Criando blocos do IDE)](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) e [Getting Started with Visual Studio – Opening a project from Source Control (Introdução ao Visual Studio – Abrindo um projeto no Controle do Código-fonte)](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3) para obter mais informações.

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>janela Saída
A janela **Saída** é onde o Visual Studio envia suas notificações, como mensagens de erro e de depuração, avisos do compilador, mensagens de status de publicação e mais. Cada tipo de mensagem tem sua própria guia.

![janela Saída](../ide/media/VSIDE_OutputWindow.png)

Para saber mais sobre como usar a janela de Saída para depuração, consulte [The Output window while debugging with Visual Studio (A Janela de Saída ao depurar com o Visual Studio)](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/).

## <a name="first-steps"></a>Primeiras etapas
- **Instalação** – para aprender a baixar e a configurar o Visual Studio, consulte [Configuração e instalação](https://go.microsoft.com/fwlink/?linkid=833223).
- **Noções básicas** – para saber mais sobre o funcionamento do Visual Studio, consulte [Introdução ao desenvolvimento com o Visual Studio](../ide/get-started-developing-with-visual-studio.md).
- **Configurações** – personalize o Visual Studio da maneira como você gosta de trabalhar. Consulte [Personalizando o IDE do Visual Studio](https://msdn.microsoft.com/en-us/library/mt269425.aspx).
- **Tutoriais** – para saber mais sobre como desenvolver um código no Visual Studio, consulte um tutorial, como [Introdução ao Visual C# e Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171.aspx) ou [Introdução à linguagem C++ no Visual Studio](https://msdn.microsoft.com/en-us/library/jj620919.aspx).
- **Vídeos** – para saber mais sobre outros recursos e aspectos do Visual Studio, confira vídeos sobre o [Canal do Microsoft Visual Studio](https://www.youtube.com/user/VisualStudio/videos) no YouTube ou vídeos do Visual Studio no [Channel 9](https://channel9.msdn.com/Tags/visual+studio).

## <a name="access-cloud-based-resources"></a>Acessar recursos baseados em nuvem

Se você desejar usar os recursos baseados em nuvem em seu aplicativo ou jogo, será possível fazer isso incluindo [os serviços do Azure](https://azure.microsoft.com/en-us/services/). É possível obter o SDK do Azure para .NET, instalando a carga de trabalho do Azure por meio do novo instalador do Visual Studio. Os pacotes que são instalados estão no mesmo nível de recurso da versão 2.9.5 do SDK. Para esta versão do Visual Studio e todas as versões futuras, o Azure SDK para .NET só estará disponível pelo instalador do Visual Studio.

Depois de instalar o SDK do Azure para .NET, uma nova janela de ferramentas ficará disponível no Visual Studio chamada **Cloud Explorer**. O Cloud Explorer permite procurar e gerenciar seus ativos e recursos do Azure de dentro do Visual Studio. Se uma determinada operação requer o portal do Azure, o Cloud Explorer fornece links que levam você até o local no portal do Azure que você precisa ir.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

Para saber mais sobre o uso do Cloud Explorer, consulte [Gerenciamento de recursos do Azure com o Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
Instalar o SDK do Azure também oferece [Ferramentas do Visual Studio para Azure](https://www.visualstudio.com/vs/azure-tools/), bem como outras ferramentas.

## <a name="tips-and-tricks"></a>Dicas e truques
Para obter atalhos e dicas e truques práticos sobre como aproveitar ao máximo o Visual Studio, consulte os sites a seguir.
- [Introdução ao Visual Studio – Dicas e Truques](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4)
- [Dicas de produtividade para o Visual Studio](https://msdn.microsoft.com/en-us/library/jj153218.aspx)
- [Dicas e truques sobre o Visual Studio](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)
- [Dicas e truques de depuração de C++](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks)
- [Getting Started with Visual Studio – Installing Visual Studio extensions (Introdução ao Visual Studio – Instalando extensões do Visual Studio)](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7)



<!--HONumber=Feb17_HO4-->


