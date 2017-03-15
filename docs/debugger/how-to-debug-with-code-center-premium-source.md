---
title: "Como depurar com a origem do Code Center Premium | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
helpviewer_keywords: 
  - "Code Center Premium"
  - "depurando [Visual Studio], Code Center Premium"
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar com a origem do Code Center Premium
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Com o depurador do [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], você pode depurar a origem compartilhada segura do Microsoft MSDN Code Center Premium.  
  
 Este tópico explica como configurar e depurar o código\-fonte superior do Code Center Premium no Visual Studio.  
  
### Para preparar para depurar com o Code Center Premium  
  
1.  Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2.  Inicie o Visual Studio.  
  
3.  No menu **Ferramentas**, clique em **Opções**.  
  
4.  Na caixa de diálogo **Opções**, abra o nó **Depuração** e clique em **Geral**.  
  
5.  Desmarque a caixa de seleção **Habilitar Apenas Meu Código \(Gerenciado Somente\)**.  
  
6.  Selecione **Habilitar Suporte a Servidor de Código\-fonte**.  
  
7.  Desmarque **Requerer que os arquivos de código\-fonte correspondam exatamente à versão original**.  
  
8.  No nó **Depuração**, clique em **Símbolos**.  
  
9. Na caixa **Locais do Arquivo de Símbolo \(.pdb\)**, desmarque a caixa de seleção **Servidores de Símbolo Microsoft** e adicione os seguintes locais:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Inclua a barra à direita **\/** no final do caminho.  
  
     Mova esses locais até a parte superior da lista para garantir que os símbolos sejam carregados primeiro.  
  
    > [!NOTE]
    >  Esses locais do Code Center Premium devem ser listados primeiro para que sejam os primeiros locais a serem carregados.  No Visual Studio 2010, você não pode mover servidores acima de entrada **Servidores de Símbolo Microsoft**, motivo pelo qual você deve desmarcar a caixa de seleção.  
    >   
    >  Para carregar símbolos dos símbolos Microsoft durante uma sessão de depuração, faça isso:  
    >   
    >  1.  No menu **Depurar**, escolha **Janelas** e clique em **Módulos**.  
    > 2.  Selecione o módulo para o qual você deseja símbolos e abra o menu de atalho.  Escolha **Carregar Símbolos de** e escolha **Servidores de Símbolo Microsoft**.  
  
10. Na caixa **Armazenar em cache os símbolos neste diretório**, insira um local como `C:\symbols` onde o Code Center Premium pode armazenar em cache os símbolos.  O armazenamento em cache dos símbolos pode melhorar significativamente o desempenho durante a depuração.  
  
     Se você tiver dificuldade para depurar código\-fonte com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depois de concluir este procedimento, verifique o local do cache para arquivos previamente armazenados em cache e arquivos de símbolo desatualizados.  Remova os arquivos antigos desatualizados.  
  
11. Clique em **OK**.  
  
12. Reinicie o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para assegurar que as configurações persistiram.  
  
### Para depurar seu código\-fonte usando Anexar ao Processo  
  
1.  Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2.  Inicie o Visual Studio.  
  
3.  Abra seu projeto do Visual Studio.  
  
4.  No menu **Ferramentas**, clique em **Anexar ao Processo**.  
  
5.  Na caixa de diálogo **Anexar ao Processo**, clique em **Selecionar**.  
  
6.  Na caixa de diálogo **Selecionar Tipo de Código**, em **Detectar estes tipos de código**, selecione **Nativo**, **Gerenciado** e **Gerenciado \(v4.0\)**.  
  
7.  Clique em **OK** para ignorar a caixa de diálogo **Selecionar Tipo de Código**.  
  
8.  Na caixa **Processos Disponíveis**, selecione o processo que você deseja depurar.  
  
9. Clique em **Anexar**.  
  
10. Quando você é solicitado a confirmar seu certificado, clique **OK**.  Em seguida, insira seu PIN.  Aceite os termos de uso do Code Center Premium, se for solicitado.  
  
     O download de símbolos pode demorar muito tempo, dependendo da velocidade da rede.  A barra de status indica quando todos os símbolos foram baixados com êxito.  
  
11. Repita as etapas de anexação para todos os projetos gerenciados em sua solução.  
  
### Para depurar o código\-fonte de uma solução existente  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho da solução e selecione **Propriedades**.  
  
2.  Na caixa de diálogo Páginas de Propriedades de Solução, escolha **Depurar Arquivos Fonte** no nó **Propriedades Comuns**.  
  
3.  Adicione o seguinte local à lista **Diretórios que contêm arquivos de origem**:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Inclua a barra à direita **\/** no final do caminho.  
  
4.  Para cada projeto gerenciado na sua solução, faça o seguinte  
  
    1.  No Gerenciador de Soluções, abra o menu de atalho do projeto e selecione **Propriedades**.  
  
    2.  Selecione **Depurar** e escolha **Habilitar depuração de código não gerenciado**.  
  
### Para depurar sua solução com código do Code Center Premium  
  
1.  Na sua classe `Package`, defina um ponto de interrupção no construtor do pacote.  
  
2.  No menu `Debug`, clique em **Iniciar Depuração**.  
  
3.  Quando atingir o ponto de interrupção no construtor de pacote, vá para a janela **Pilha de Chamadas** e clique com o botão direito do mouse no registro de ativação do assembly do qual você deseja carregar símbolos e clique em **Carregar Símbolos**.  
  
     Clique duas vezes no quadro de chamada para carregar a origem.  
  
### Para procurar o código\-fonte no Code Center Premium  
  
1.  Conecte seu leitor de cartão inteligente e insira o cartão obtido da Shared Source Initiative.  
  
2.  Inicie o Internet Explorer e insira esta URL: `https://codepremium.msdn.microsoft.com`  
  
3.  Navegue para encontrar a fonte que você deseja.  
  
## Consulte também  
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)