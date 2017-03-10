---
title: "Organizar objetos em cont&#234;ineres de layout no XAML Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Organizar objetos em cont&#234;ineres de layout no XAML Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Imagine onde quer que os objetos sejam exibidos em uma página. objetos, como imagens, botões e vídeos.  Talvez você queira que eles sejam exibidos em linhas e colunas em uma única linha vertical ou horizontalmente ou em posições fixas.  
  
 Depois que você teve a oportunidade de se pensar em como a página poderá aparecer, escolha um painel de layout.  Todas as páginas começar com uma porque você precisa de algo para adicionar seus objetos.  Por padrão, é um **grade** mas você pode alterá\-lo.  
  
 Painéis de layout ajudarão\-lo a organizar os objetos em uma página, mas fazem mais do que isso.  Eles ajudam você a projetar para diferentes tamanhos de tela e resoluções.  Quando os usuários executam seu aplicativo, tudo em um painel de layout é redimensionada para corresponder o espaço na tela de seu dispositivo.  É claro que, se não quiser que o layout para fazer isso, você pode substituir esse comportamento para uma parte do layout, ou todo o layout.  Você pode usar propriedades de altura e largura para controlar o que.  
  
 Esta página descreve controles e painéis de layout e, em seguida, direciona a vídeos curtos que o ajudarão a começar com eles.  
  
> [!NOTE]
>  Alguns dos vídeos podem se referir a mesclagem ou Expression Blend, que usam o mesmo XAML designer Visual Studio e Blend para Visual Studio.  
  
## Painéis de layout  
 Sua página inicial, escolhendo um desses painéis de layout.  A página pode ter mais de um.  Por exemplo, você pode começar com um **grade** layout do painel e, em seguida, adicione um **StackPanel** para uma área a **grade** para que você pode organizar controles verticalmente no elemento.  
  
 Os seguintes painéis de layout são mais popularmente usado, mas existem outras.  Você pode encontrá\-los em todos o **ativos** painel.  
  
-   [Grelha](#Grid)  
  
-   [UniformGrid](#Uniform)  
  
-   [Tela](#Canvas)  
  
-   [StackPanel](#Stack)  
  
-   [WrapPanel](#Wrap)  
  
-   [DockPanel](#Dock)  
  
###  <a name="Grid"></a> Grelha  
 Organize objetos em linhas e colunas.  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [usando grades](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids)  
  
###  <a name="Uniform"></a> UniformGrid  
 Organize objetos em regiões de grade iguais ou uniformes.  Este painel é excelente para organizar uma lista de imagens.  
  
 \(Disponível somente para projetos WPF\)  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabalhando com um UniformGrid](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid)  
  
###  <a name="Canvas"></a> Tela  
 Organize objetos como desejar.  Quando os usuários executam seu aplicativo, esses elementos serão corrigiram posições na tela.  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [trabalhar com a tela](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas)  
  
###  <a name="Stack"></a> StackPanel  
 Organize objetos em uma única linha horizontal ou verticalmente.  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabalhando com StackPanel e WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Wrap"></a> WrapPanel  
 Organize objetos em sequência da esquerda para a direita.  Quando o painel fica sem espaço na borda da extrema direita, ele *quebra* o conteúdo para a próxima linha, e assim por diante da esquerda para a direita, de cima para baixo.  Você também pode fazer a orientação de um painel wrap vertical para que objetos fluem de cima para baixo, esquerda para a direita.  
  
 \(Disponível somente para projetos WPF\)  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabalhando com StackPanel e WrapPanel](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel)  
  
###  <a name="Dock"></a> DockPanel  
 Organizar os objetos para que permaneçam, ou *Encaixar*, em uma borda do painel.  
  
 \(Disponível somente para projetos WPF\)  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [WPF \- DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)  
  
## Controles de layout  
 Você pode adicionar objetos a controles de layout.  Eles não são como rico em um painel de layout, mas você pode encontrá\-los úteis para determinados cenários.  
  
 Os seguintes controles de layout são mais popularmente usado, mas existem outras.  Você pode encontrá\-los em todos o **ativos** painel.  
  
-   [Borda](#Border)  
  
-   [Popup](#Popup)  
  
-   [ScrollViewer](#Scroll)  
  
-   [UniformGrid](#Uniform)  
  
-   [Viewbox](#View)  
  
###  <a name="Border"></a> Borda  
 Crie uma borda, plano de fundo ou ambos em torno de um objeto.  Você pode adicionar apenas um objeto para um **borda**.  Se você deseja aplicar uma borda ou um plano de fundo para mais de um objeto, adicione o painel de layout para o **borda**.  Em seguida, adicione objetos a esse painel ou controle.  
  
 **Assistir a um vídeo curto:** ![Configurar recursos instalados](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabalhando com bordas](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders)  
  
###  <a name="Popup"></a> Popup  
 Mostra informações ou opções para usuários em uma janela.  Você pode adicionar apenas um objeto para um **pop\-up**.  Por padrão, um **pop\-up** contém um **grade** mas você pode alterá\-lo.  
  
###  <a name="Scroll"></a> ScrollViewer  
 Habilitar usa para rolar para baixo de uma página ou a área de uma página.  Você pode adicionar apenas um objeto para um **ScrollViewer** faz muito sentido para adicionar um painel de layout, como um **grade** ou **StackPanel**.  
  
###  <a name="View"></a> Viewbox  
 Dimensionar objetos, assim como você faria com um controle de zoom.  Você pode adicionar apenas um objeto para um **Viewbox**.  Se você quiser aplicar esse efeito a mais de um objeto, adicionar um painel de layout para o **ViewBox**, e, em seguida, adicionar os controles para o painel de layout.  
  
 \(Disponível somente para projetos WPF\)  
  
## Consulte também  
 [Trabalhando com elementos no Designer XAML](../designers/working-with-elements-in-xaml-designer.md)   
 [Criando uma interface de usuário usando o Designer XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)