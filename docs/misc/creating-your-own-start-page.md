---
title: "Criando sua pr&#243;pria p&#225;gina inicial | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Criar página de início"
  - "página inicial personalizada"
  - "Personalizar página inicial"
ms.assetid: a0df5b9c-0932-4e54-86f0-28530ad9d684
caps.latest.revision: 22
caps.handback.revision: 22
manager: "douge"
---
# Criando sua pr&#243;pria p&#225;gina inicial
Você pode criar uma página de início personalizados usando o modelo de projeto de página Iniciar ou criando uma página em branco do início.  
  
 O designer XAML pode não fornecer representações visuais totalmente precisas das páginas personalizadas de iniciar devido a dependências no modelo de aplicativo do Visual Studio.  
  
## Usando o modelo de projeto  
 O modelo de projeto de página inicial cria um projeto de página inicial que é uma cópia completa do Visual Studio Start Page. Você pode editar a página de início às suas especificações.  
  
#### Para criar uma página de início personalizados usando o modelo de projeto de página inicial  
  
1.  Baixe e instale o [modelo de projeto de página inicial](http://go.microsoft.com/fwlink/?LinkId=186204) da Galeria do Visual Studio.  
  
    > [!WARNING]
    >  Neste momento o modelo de projeto do Visual Studio 2010 Start Page não foi atualizado. Para obter informações sobre como atualizar esse modelo, consulte [Como: atualizar uma página de início personalizado do Visual Studio](../Topic/How%20to:%20Upgrade%20a%20Visual%20Studio%20Custom%20Start%20Page.md).  
  
2.  Depois de ter instalado o modelo, crie um novo projeto de página de início com ele.  
  
3.  No painel esquerdo da caixa de diálogo Novo projeto, em **modelos instalados**, expanda o **Other Project Types** nó e clique **extensibilidade**.  
  
4.  No painel central, clique em **página de início personalizado**, nomeie o projeto e clique em **OK**.  
  
     Visual Studio cria um projeto de página inicial que é uma cópia completa do Visual Studio Start Page.  
  
5.  De **Solution Explorer**, abra **StartPage**.  
  
6.  Edite o XAML.  
  
     Você pode exibir seu trabalho pressionando F5 para abrir uma instância experimental do Visual Studio com a página de início personalizado instalado.  
  
## Criando uma página em branco inicial  
 A maneira mais fácil para criar uma página em branco inicial é usar o modelo de projeto de página inicial e, em seguida, remover o conteúdo.  
  
#### Para criar uma página em branco inicial usando o modelo de projeto de página inicial  
  
1.  Crie um projeto de página inicial usando o modelo de projeto de página inicial, conforme descrito no procedimento anterior.  
  
2.  Abra o XAML.  
  
3.  Remover todo o conteúdo da página, deixando apenas os elementos xml externo e a grade contendo <xref:System.Windows.Controls.Grid> elemento, para que seu arquivo. XAML é semelhante ao exemplo a seguir.  
  
     [!CODE [BlankStartPage#01](../CodeSnippet/VS_Snippets_VSSDK/blankstartpage#01)]  
  
4.  Remova os arquivos de suporte que você não pretende usar.  
  
     Você deve manter os arquivos. VSIX e pkgdef para fins de implantação.  
  
 Como alternativa, você pode criar uma página em branco Iniciar criando um arquivo XAML com a estrutura de marca correto seja reconhecida pelo Visual Studio. Você pode adicionar marcação e code\-behind para obter a aparência desejada e a funcionalidade. Para obter mais informações, consulte [Criando uma página inicial personalizada](../extensibility/creating-a-custom-start-page.md).  
  
## Página inicial do teste e aplicando personalizado  
 Não defina a instância primária para executar a página de início personalizado até que você verificar que ele não falhe. Depois de testar sua página de início personalizados, aplicá\-lo ao seu sistema, repetindo as três últimas etapas deste procedimento na instância principal do Visual Studio.  
  
#### Para testar uma página de início personalizado  
  
1.  Pressione F5.  
  
     A instância experimental do Visual Studio é aberto com a nova página inicial instalado, mas não selecionada.  
  
2.  Na instância experimental do Visual Studio, no **ferramentas** menu, clique em **opções**.  
  
3.  No **opções** caixa de diálogo **ambiente**, selecione **inicialização**. Em seguida, no **Personalizar página inicial** lista, selecione o arquivo. XAML e clique em **OK**.  
  
4.  Sobre o **exibição** menu, clique em **Start Page**.  
  
     O página de início de trabalho é exibido. Feche a instância experimental, copiar novamente os arquivos alterados e, em seguida, abra novamente a instância experimental para ver as novas alterações.  
  
 Você pode compartilhar sua página de início personalizado carregando o arquivo. VSIX do diretório bin\\debug para o [Galeria do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site da Web ou para outro site da Web ou intranet compartilhar. Para obter mais informações, consulte [Implantação de páginas de início personalizado](../extensibility/deploying-custom-start-pages.md).  
  
## Consulte também  
 [Personalizando a página inicial](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Passo a passo: Adicionando XAML personalizado para a página inicial](../Topic/Walkthrough:%20Adding%20Custom%20XAML%20to%20the%20Start%20Page.md)