---
title: "Janelas de mem&#243;ria | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.memory"
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
  - "buffers, exibindo"
  - "depurador [Visual Studio], Janela Memória"
  - "depurando [Visual Studio], Janela Memória"
  - "memória [Visual Studio ], depuração"
  - "Janela Memória"
  - "cadeias de caracteres [Visual Studio], exibindo"
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Janelas de mem&#243;ria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A janela **Memória** fornece uma exibição no espaço de memória usado pelo seu aplicativo.  A janela **Inspeção**, a caixa de diálogo **QuickWatch**, a janela **Autos** e a janela **Locais** mostram o conteúdo de variáveis, que são armazenadas em locais específicos na memória.  Mas a janela **Memória** mostra a imagem em grande escala.  Esta exibição pode ser conveniente para examinar grandes partes de dados \(buffers ou grandes cadeias de caracteres, por exemplo\) que não são exibidas corretamente nas outras janelas.  Entretanto, a janela **Memória** não é limitada para exibir dados.  Ela exibirá tudo no espaço de memória, não importa se o conteúdo for dados, código ou bits aleatórios de lixo na memória não atribuída.  
  
 A janela **Memória** estará disponível apenas se a depuração do nível de endereços estiver habilitada na caixa de diálogo **Opções**, nó **Depuração**.  A janela **Memória** não está disponível para Script ou SQL, que são as linguagens que não reconhecem o conceito de memória.  
  
## Abrindo uma janela de memória  
  
#### Para abrir uma janela de memória  
  
1.  Inicie a depuração, se você já não estiver no modo de depuração.  
  
2.  No menu **Depurar**, aponte para **Janelas**.  Em seguida, aponte para **Memória** e clique em **Memória 1**, **Memória 2**, **Memória 3** ou **Memória 4**. \(As edições de nível inferior do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] têm apenas uma única janela **Memória**.  Se você estiver usando uma dessas edições, basta clicar em **Memória**\).  
  
## Paginação na janela de memória  
 A janela **Memória** tem uma barra de rolagem vertical que opera de uma maneira não padrão.  O espaço de endereço de um computador moderno é muito grande e você pode preferir arrastar a caixa de rolagem para um local aleatório.  Por esse motivo, a caixa de rolagem é carregada e sempre permanece no centro da barra de rolagem.  Em aplicativos de código nativo, você pode rolar a página para cima ou para baixo, mas não pode rolar livremente.  
  
 Um endereço de memória mais alto aparece na parte inferior da janela.  Para exibir um endereço mais alto, role para baixo, não para cima.  
  
#### Para mover para cima ou para baixo na memória  
  
1.  Para rolar a página para baixo \(mover para um endereço de memória mais alto\), clique abaixo da caixa de rolagem na barra de rolagem vertical.  
  
2.  Para rolar a página para cima \(mover para um endereço de memória mais baixo\), clique acima da caixa de rolagem na barra de rolagem vertical.  
  
## Selecionando um local de memória  
 Se você quiser mover imediatamente para um local selecionado na memória, poderá fazer isso usando uma operação de arrastar e soltar ou editando o valor na caixa **Endereço**.  A caixa **Endereço** não aceita somente valores numéricos, mas também expressões que são avaliadas como endereços.  Por padrão, a janela **Memória** trata uma expressão **Endereço** como uma expressão dinâmica, que é reavaliada à medida que seu programa é executado.  As expressões dinâmicas podem ser muito úteis.  Por exemplo, você pode usá\-las para exibir a memória que é tocada por um ponteiro.  
  
#### Para selecionar um local de memória arrastando e soltando  
  
1.  Em qualquer janela, selecione um endereço de memória ou variável de ponteiro que contém um endereço de memória.  
  
2.  Arraste o endereço ou ponteiro para a janela **Memória**.  
  
#### Para selecionar um local de memória editando  
  
1.  Na janela **Memória**, marque a caixa **Endereço**.  
  
2.  Digite ou cole o endereço que você quer ver e pressione **ENTER**.  
  
## Alterando o modo como a janela de memória exibe informações  
 Você pode personalizar a maneira como a janela **Memória** mostra o conteúdo da memória.  Por padrão, o conteúdo da memória aparece como inteiros de um byte em formato hexadecimal e o número de colunas é determinado automaticamente pela largura atual da janela.  
  
#### Para alterar o formato do conteúdo de memória  
  
1.  Clique com o botão direito na janela **Memória**.  
  
2.  Escolha o formato que você deseja.  
  
#### Para alterar o número de colunas na janela de memória  
  
1.  Na barra de ferramentas na parte superior da janela **Memória**, localize a lista **Colunas**.  
  
2.  Na lista **Colunas**, selecione o número de colunas que você deseja exibir ou selecione **Automático** para ajustar automaticamente na largura da janela.  
  
 Se não quiser que o conteúdo da janela **Memória** seja alterado à medida que seu programa é executado, você poderá desativar a avaliação da expressão dinâmica.  
  
#### Para ativar\/desativar a avaliação dinâmica  
  
1.  Clique com o botão direito na janela **Memória**.  
  
2.  No menu de atalho exibido, clique em **Reavaliar Automaticamente**.  
  
     Se a avaliação dinâmica estiver ativa, a opção será selecionada e clicar nela a desativará.  Se a avaliação dinâmica estiver inativa, a opção não será selecionada e clicar nela a ativará.  
  
 Você pode ocultar ou exibir a barra de ferramentas na parte superior da janela **Memória**.  Você não terá acesso à caixa de endereço ou outras ferramentas enquanto a barra de ferramentas estiver oculta.  
  
#### Para ativar\/desativar a barra de ferramentas  
  
1.  Clique com o botão direito em uma janela **Memória**.  
  
2.  No menu de atalho, clique em **Mostrar Barra de Ferramentas**.  
  
     A barra de ferramentas é exibida ou desaparece, dependendo do seu estado anterior.  
  
## Seguindo um ponteiro pela memória  
 Em aplicativos de código nativo, você poderá usar nomes de registro como expressões dinâmicas.  Por exemplo, você pode usar o ponteiro de pilhas para seguir a pilha.  
  
#### Para seguir um ponteiro pela memória  
  
1.  Na caixa **Endereço** da janela **Memória**, digite uma expressão de ponteiro.  A variável de ponteiro deve estar no escopo atual.  Dependendo da linguagem, você poderá ter que remover a referência a ele.  
  
2.  Pressione **ENTER**.  
  
     Agora, quando você usa um comando de execução, como, por exemplo, **Etapa**, o endereço de memória que é exibido mudará automaticamente quando o ponteiro for alterado.  
  
## Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)