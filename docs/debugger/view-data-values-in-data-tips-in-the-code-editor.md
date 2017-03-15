---
title: "Exibir valores de dados em Dicas de Dados no editor de c&#243;digos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Ferramenta DataTips"
  - "depurando [Visual Studio], DataTips"
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibir valores de dados em Dicas de Dados no editor de c&#243;digos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os DataTips fornecem um modo conveniente de exibir informações sobre variáveis em seu programa durante a depuração.  Os DataTips funcionam apenas no modo de interrupção e apenas com variáveis que estejam no escopo de execução atual.  
  
 No [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], os DataTips podem ser fixados em um local específico em um arquivo de origem ou podem flutuar sobre todas as janelas do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Para exibir um DataTip \(somente no modo de interrupção\)  
  
1.  Em uma janela de origem, coloque o ponteiro do mouse sobre qualquer variável no escopo atual.  
  
     Um DataTip aparece.  
  
    > [!NOTE]
    >  Os DataTips são sempre avaliados no contexto onde a execução é suspensa e não por onde o cursor está passando.  Se você passar o mouse sobre uma variável em outra função com o mesmo nome de uma variável que está no contexto atual, o valor da variável na outra função será exibido como o valor da variável no contexto atual.  
  
2.  O DataTip desaparecerá quando você remover o ponteiro do mouse.  Para fixar o DataTip de modo que permaneça aberto, clique no ícone **Fixar à origem** ou  
  
    -   Clique com o botão direito do mouse em uma variável e clique **Fixar à origem**.  
  
     O DataTip fixado é fechado quando a sessão de depuração termina.  
  
### Para desafixar um DataTip e fazê\-lo flutuar  
  
-   Em um DataTip fixado, clique no ícone **Desafixar da origem**.  
  
     O ícone de fixar é alterado para a posição desafixada.  O DataTip agora flutua sobre todas as janelas abertas.  O DataTip flutuante é fechado quando a sessão de depuração termina.  
  
### Ao refixar um DataTip flutuante  
  
-   Em um DataTip, clique no ícone de fixar.  
  
     O ícone de fixar é alterado para a posição fixada.  Se o DataTip estiver fora de uma janela de origem, o ícone de fixar estará desabilitado e o DataTip não poderá ser fixado.  
  
### Para fechar um DataTip  
  
-   Coloque o ponteiro do mouse sobre um DataTip e clique no ícone **Fechar**.  
  
### Para fechar todos os DataTips  
  
-   No menu **Depurar**, clique em **Limpar Todos os DataTips**.  
  
### Para fechar todos os DataTips para um arquivo específico  
  
-   No menu **Depurar**, clique em **Limpar Todos os DataTips Fixados no** *File*.  
  
## Expandindo e editando as informações  
 Você pode usar os DataTips para expandir uma matriz, uma estrutura ou um objeto para exibir seus membros.  Você também pode editar o valor de uma variável de um DataTip.  
  
#### Para expandir uma variável para ver seus elementos  
  
-   Em um DataTip, coloque o ponteiro do mouse no sinal de **\+** que vem antes do nome da variável.  
  
     A variável expande para mostrar seus elementos na forma da árvore.  
  
     Quando a variável é expandida, você poderá usar as teclas de direção no teclado para mover para cima e para baixo.  Outra opção é usar o mouse.  
  
#### Para editar o valor de uma variável usando um DataTip  
  
1.  Em um DataTip, clique no valor.  Isso está desabilitado para valores somente leitura.  
  
2.  Digite um novo valor e pressione ENTER.  
  
## Criando um DataTip transparente  
 Se quiser ver o código que está por trás de um DataTip, poderá criar o DataTip temporariamente transparente.  Isso não se aplica a DataTips fixados ou flutuantes.  
  
#### Para criar um DataTip transparente  
  
-   Em um DataTip, pressione CTRL.  
  
     O DataTip permanecerá transparente enquanto você mantiver pressionada a tecla CTRL.  
  
## Visualizando tipos de dados complexos  
 Se um ícone de lupa aparecer ao lado do nome de variável em um DataTip, um ou mais [Visualizadores](../debugger/create-custom-visualizers-of-data.md) estarão disponíveis para variáveis desse tipo de dados.  Você pode usar um visualizador para exibir informações de uma maneira mais significativa, geralmente gráfica.  
  
#### Para exibir o conteúdo de uma variável usando um visualizador  
  
-   Clique no ícone de lupa para selecionar o visualizador padrão para o tipo de dados.  
  
     \-ou\-  
  
     Clique na seta do menu suspenso ao lado do visualizador para selecionar de uma lista de visualizadores apropriados para o tipo de dados.  
  
     Um visualizador exibe as informações.  
  
## Adicionando informações a uma janela Inspeção  
 Se você quiser continuar a inspecionar uma variável, poderá adicionar a variável à janela **Inspeção** de um DataTip.  
  
#### Para adicionar uma variável à janela Inspeção  
  
-   Clique com o botão direito em um DataTip e clique em **Adicionar Inspeção**.  
  
     A variável é adicionada à janela **Inspeção**.  Se você estiver usando uma edição que dá suporte a várias janelas de **Inspeção**, a variável será adicionada a **Inspeção 1.**  
  
## Importando e exportando DataTips  
 Você pode exportar DataTips para um arquivo XML, que pode ser compartilhado com um colega ou editado por um editor de texto.  
  
#### Para exportar DataTips  
  
1.  No menu Depurar, clique em **Exportar DataTips**.  
  
     A caixa de diálogo **Exportar DataTips** aparece.  
  
2.  Use técnicas de arquivo padrão para navegar até o local onde você deseja salvar o arquivo XML, digite um nome para o arquivo na caixa **Nome do arquivo** e clique em **OK**.  
  
#### Para importar DataTips  
  
1.  No menu Depurar, clique em **Importar DataTips**.  
  
     A caixa de diálogo **Importar DataTips** aparece.  
  
2.  Use a caixa de diálogo para localizar o arquivo XML que você deseja abrir e clique em **OK**.  
  
## Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Como usar a caixa de diálogo QuickWatch](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Como alterar o formato numérico das janelas do depurador](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)