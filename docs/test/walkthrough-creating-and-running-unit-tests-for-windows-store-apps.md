---
title: "Explica&#231;&#227;o passo a passo: Criando e executando testes de unidade de aplicativos da Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "testes de unidade, criando"
  - "testes de unidade"
  - "testes de unidade, aplicativos da Windows Store"
  - "testes de unidade, em execução"
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "mlearned"
manager: "douge"
---
# Explica&#231;&#227;o passo a passo: Criando e executando testes de unidade de aplicativos da Windows Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio inclui suporte para testes de unidade gerenciados [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos e inclui modelos de biblioteca de teste de unidade para o Visual c\#, Visual Basic e Visual C\+\+.  
  
> [!TIP]
>  Para obter mais informações sobre como desenvolver [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos, consulte [Introdução aos aplicativos da Windows Store](http://go.microsoft.com/fwlink/?LinkID=241410).  
  
 O Visual Studio fornece a seguinte funcionalidade de teste de unidade:  
  
-   [Criar projetos de teste de unidade](#CreateAndRunUnitTestWin8Tailored_Create)  
  
-   [Editar o manifesto para o projeto de teste de unidade](#CreateAndRunUnitTestWin8Tailored_Manifest)  
  
-   [Codificar o Teste de Unidade](#CreateAndRunUnitTestWin8Tailored_Code)  
  
-   [Executar testes de unidade](#CreateAndRunUnitTestWin8Tailored_Run)  
  
 Os procedimentos a seguir descrevem as etapas para criar, executar e depurar testes de unidade para o Windows 8 gerenciado [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativo.  
  
## Pré-requisitos  
 Visual Studio  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Create"></a> Criar projetos de teste de unidade  
  
#### Para criar um projeto de teste de unidade para um aplicativo da Windows Store  
  
1.  Do **arquivo** menu, escolha **novo projeto**.  
  
     Exibe a caixa de diálogo Novo projeto.  
  
2.  Em modelos, escolha a linguagem de programação que você deseja criar o teste de unidade e escolha associado [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] biblioteca de teste de unidade. Por exemplo, escolha **Visual C\#** , em seguida, escolha **da Windows Store**, e, em seguida, escolha **biblioteca de teste de unidade \(aplicativos da Windows Store\)**.  
  
    > [!NOTE]
    >  Visual Studio inclui modelos de biblioteca de teste de unidade para o Visual c\#, Visual Basic e Visual C\+\+.  
  
3.  \(Opcional\) No **nome** caixa de texto, digite o nome que você deseja usar para o [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]projeto de teste de unidade.  
  
4.  \(Opcional\) Modifique o caminho onde você deseja criar o projeto para confirmá\-la no **local** caixa de texto, ou escolher o **Procurar** botão.  
  
5.  \(Opcional\) No **solução** nome da caixa de texto, digite esse nome que você deseja usar para sua solução.  
  
6.  Deixe o **criar diretório para solução** opção selecionada e escolha o **OK** botão.  
  
     ![Biblioteca de teste de unidade sob medida](../test/media/unit_test_win8_1.png "Unit\_Test\_Win8\_1")  
  
     Gerenciador de soluções é preenchida com os novos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]projeto de teste de unidade e o editor de códigos exibe o teste de unidade padrão intitulado UnitTest1.  
  
     ![Novo projeto de teste de unidade sob medida](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png "Unit\_Test\_Win8\_UnitTestExplorer\_NewProjectCreated")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a> Editar o manifesto para o projeto de teste de unidade  
 Pode ser necessário editar o manifesto para o projeto de teste de unidade fornecer os recursos necessários para executar o aplicativo.  
  
#### Para editar o arquivo manifesto do aplicativo do projeto de teste de unidade da Windows Store  
  
1.  No Solution Explorer, no novo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projeto de teste de unidade, atualizarei o arquivo de atalho e escolha **Abrir**.  
  
     Exibe o Designer de manifesto para edição.  
  
2.  No Designer de manifesto, escolha o **recursos** guia.  
  
3.  Na lista em **recursos**, selecione os recursos que você precisa de seu teste de unidade e o código que teste para que a TI. Por exemplo, selecione o **Internet** caixa de seleção se o teste de unidade precisa e o código que está testando precisa ter a capacidade de acessar a internet.  
  
    > [!NOTE]
    >  Os recursos que você selecionar devem incluir somente os recursos necessários para o [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] teste de unidade para funcionar corretamente. Os recursos nunca deverá incluir os recursos que não são parte do [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativo sendo testados e geralmente deve ser um subconjunto dos recursos especificados para o [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]aplicativo em teste.  
  
     Para obter mais informações sobre o Designer de manifesto, consulte [Configurar um pacote do aplicativo do Windows 8.1 usando o designer de manifesto](../Topic/Configure%20a%20Windows%208.1%20app%20package%20by%20using%20the%20manifest%20designer.md).  
  
     ![Manifesto de teste de unidade](../test/media/unit_test_win8_.png "Unit\_Test\_Win8\_")  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Code"></a> Codificar o Teste de Unidade  
  
#### Código de teste de unidade para um aplicativo da Windows Store  
  
1.  No Editor de código, edite o teste de unidade e adicione as declarações e a lógica necessária para o teste.  
  
     Para obter mais informações, consulte [usando as Classes Assert](http://go.microsoft.com/fwlink/?LinkID=224991) na biblioteca MSDN.  
  
##  <a name="CreateAndRunUnitTestWin8Tailored_Run"></a> Executar testes de unidade  
  
#### Para compilar a solução e executar o teste de unidade usando o Gerenciador de testes  
  
1.  Sobre o **teste** menu, escolha **Windows**, e, em seguida, escolha **Test Explorer**.  
  
     Teste Explorer exibirá sem o teste seja listado.  
  
2.  Do **criar** menu, escolha **Build Solution**.  
  
     O teste de unidade agora está listado.  
  
    > [!NOTE]
    >  Você deve criar a solução para atualizar a lista de testes de unidade no Gerenciador de testes.  
  
    > [!WARNING]
    >  Visual Studio problema conhecido: você deve abrir o Gerenciador de testes antes de criar o projeto de teste.  
  
3.  No Gerenciador de testes, escolha o teste de unidade que você criou.  
  
    > [!TIP]
    >  O Gerenciador de testes fornece um link para o código\-fonte lado **fonte:**.  
  
4.  Escolha **Executar todos**.  
  
     ![Explorer de teste de unidade &#45; executar teste de unidade](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png "Unit\_Test\_Win8\_UnitTestExplorer\_ContextMenuRun")  
  
    > [!TIP]
    >  Selecione um ou mais testes de unidade listados no Explorer e, em seguida, clique com botão direito e escolha **executar testes selecionados**.  
    >   
    >  Além disso, você pode optar por **Depurar testes selecionados**, **Abrir teste**, e usar o **propriedades** opção.  
    >   
    >  ![Unit Test Explorer &#45; uni test context menu](../test/media/unit_test_win8_unittestexplorer_contextmenu.png "Unit\_Test\_Win8\_UnitTestExplorer\_ContextMenu")  
  
     O teste de unidade é executado. Após a conclusão, o Gerenciador de testes exibe o status do teste, tempo decorrido e fornece um link para a fonte.  
  
     ![Explorer de teste de unidade &#45; teste concluído](../test/media/unit_test_win8_unittestexplorer_done.png "Unit\_Test\_Win8\_UnitTestExplorer\_Done")  
  
## Recursos externos  
  
### Vídeos  
 [Channel 9: Teste seus aplicativos da Windows Store criados com XAML de unidade](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### Fóruns  
 [Testes de unidade do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### Biblioteca MSDN  
 [Biblioteca do MSDN – criando e executando testes de unidade para código existente \(Visual Studio 2010\)](http://go.microsoft.com/fwlink/?LinkID=223683)  
  
## Consulte também  
 [Testando aplicativos da Store com o Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Compilar e testar um aplicativo da Windows Store usando o Team Foundation Build](../Topic/Build%20and%20test%20a%20Windows%20Store%20app%20using%20Team%20Foundation%20Build.md)