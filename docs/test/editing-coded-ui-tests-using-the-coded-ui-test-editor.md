---
title: "Editando testes de interface de usu&#225;rio codificada usando o editor de teste de interface de usu&#225;rio codificada | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codedUItest.testeditor"
helpviewer_keywords: 
  - "teste de IU codificado, Editor de testes de UI codificados"
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 40
caps.handback.revision: 40
ms.author: "mlearned"
manager: "douge"
---
# Editando testes de interface de usu&#225;rio codificada usando o editor de teste de interface de usu&#225;rio codificada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Editor de teste de IU codificado permite modificar facilmente os testes de UI codificados. Usando o Editor de testes de UI codificados, você pode localizar, exibir e editar as propriedades de seus métodos de teste e ações de interface do usuário. Além disso, você pode usar o mapa de controle de interface do usuário para exibir e editar seus controles correspondentes.  
  
 **Requisitos**  
  
-   Visual Studio Enterprise  
  
## Por que devo fazer isso?  
 Usar o Editor de teste de IU codificado é mais rápido e mais eficiente do que a edição do código em seus métodos de teste UI codificados usando o Editor de código. Com o teste de Editor de IU codificado, você pode usar os menus de atalho da barra de ferramentas para localizar rapidamente e modificar valores de propriedade associados aos controles e ações de interface do usuário. Por exemplo, você pode usar o código da interface do usuário do Editor de testes da barra de ferramentas para executar os seguintes comandos:  
  
 ![Edito de teste de interface do usuário](../test/media/uitesteditor.png "UITestEditor")  
  
1.  [Localizar](../ide/finding-and-replacing-text.md) ajuda a localizar controles e ações de interface do usuário.  
  
2.  [Excluir](#CodedUITestEditor_DeleteUIActions) remove ações de interface do usuário indesejadas.  
  
3.  **Renomear** altera os nomes de métodos de teste e controles.  
  
4.  **Propriedades** abre a janela de propriedades para o item selecionado.  
  
5.  [Dividir em um novo método](#CodedUITestEditor_SplitMethods) permite modularizar as ações de interface do usuário.  
  
6.  [Mover o código](#CodedUITestEditor_MoveMethods) adiciona o código personalizado para os métodos de teste.  
  
7.  [Inserir atraso antes](#CodedUITestEditor_InsertDelay) adiciona uma pausa antes de uma ação de interface do usuário, especificada em milissegundos.  
  
8.  [Localizar o controle de interface do usuário](#CodedUITestEditor_LocateUIControl) identifica o local do controle na interface do usuário do aplicativo em teste.  
  
9. [Localizar todos os](#CodedUITestEditor_LocateDecendants) ajuda a verificar controla alterações significativas para os controles do aplicativo e propriedade.  
  
## Como fazer isso?  
 Em [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], abrindo o arquivo Uitest associado ao seu teste de IU codificado no seu projeto de teste de IU codificado exibirá automaticamente o teste de IU codificado no Editor de testes de UI codificados. Os procedimentos a seguir descrevem como você pode localizar e editar seus métodos de teste e propriedades para as ações de interface do usuário e controles usando a barra de ferramentas do editor e menus de atalho.  
  
## Abra um teste de IU codificado  
 Você pode exibir e editar seu Visual C\# e teste de IU codificado com base em Visual Basic usando o Editor de testes de UI codificados.  
  
 ![Menu de contexto Editar com o código da interface do usuário teste Builder](../test/media/editcodeduitest.png "EditCodedUITest")  
  
 No Solution Explorer, abra o menu de atalho **Uitest** e escolha **Abrir**. Teste de IU codificado é exibido no Editor de testes de código da interface do usuário. Agora você pode exibir e editar os métodos gravados, ações e controles correspondentes no teste de IU codificado.  
  
> [!TIP]
>  Quando você seleciona uma ação da interface do usuário que está localizada em um método no **ações de interface do usuário** painel, o controle correspondente é realçado. Você também pode modificar a ação de interface do usuário ou as propriedades dos controles.  
  
 *Não vejo* o Editor de teste de IU codificado.  
 Você pode estar usando a versão do Visual Studio Enterprise antes de 2012. O Editor de testes de UI codificados também estava disponível no Visual Studio 2010 Feature Pack 2 com uma assinatura do MSDN.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [Microsoft Visual Studio 2010 Feature Pack 2](http://go.microsoft.com/fwlink/?LinkID=204119).  
  
##  <a name="CodedUITestEditor_EditActionAndControlProperties"></a> Modificar propriedades de ação de interface do usuário e suas propriedades correspondentes do controle  
 Usando o Editor de testes de UI codificados, você pode localizar rapidamente e exibir todas as ações de interface do usuário em seus métodos de teste. Quando você seleciona a ação de interface do usuário no editor, o controle correspondente é realçado automaticamente. Da mesma forma, se você selecionar um controle, as ações de interface do usuário associadas são realçadas. Quando você seleciona uma ação da interface do usuário ou um controle, em seguida, é fácil de usar a janela Propriedades para modificar as propriedades que correspondem com ele.  
  
 ![Propriedades de ação de interface do usuário](../test/media/codeduiedituiaction.png "CodedUIEditUIAction")  
Editar propriedades de ação de interface do usuário  
  
 Para modificar as propriedades de uma ação de interface do usuário, o **ação de interface do usuário** painel, expanda o método de teste que contém uma ação da interface do usuário que você deseja editar as propriedades, selecione a ação de interface do usuário e, em seguida, modificar as propriedades usando a janela Propriedades.  
  
 Por exemplo, se um servidor estiver indisponível, e você tem uma ação da interface do usuário associada com seu navegador da Web que estados **Ir para página da Web 'http:\/\/Contoso1\/default.aspx'**, você pode alterar a URL para `‘http://Contoso2/default.aspx’`.  
  
 ![Propriedades de controle](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp")  
Editar propriedades de controle  
  
 Modificar as propriedades de um controle é feito da mesma maneira que as ações de interface do usuário. No **mapa de controle de interface do usuário** painel, selecione o controle que você deseja editar e modificar suas propriedades usando a janela Propriedades.  
  
 Por exemplo, um desenvolvedor pode ter alterado o **\(ID\)** propriedade em um controle de botão no código\-fonte para o aplicativo que está sendo testado de "idSubmit" para "idLogin". Com o **\(ID\)** propriedade alterada no aplicativo, teste de IU codificado não será capaz de localizar o controle de botão e falhará. Nesse caso, o testador pode abrir o **Propriedades de pesquisa** coleta e altere o **Id** propriedade para coincidir com o novo valor que o desenvolvedor usado no aplicativo. O testador também pode alterar o **nome amigável** valor de propriedade de "Enviar" a "Logon". Com essa alteração, a ação de interface do usuário associada no código da interface do usuário Editor de teste é atualizada de "Botão 'Enviar' escolher" para "escolher 'Login' botão."  
  
 Depois de concluir as modificações, salve as alterações no arquivo Uimap escolhendo **Salvar** sobre o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barra de ferramentas.  
  
 *O que mais devo saber?*  
 **Dicas**  
  
-   ![Dica](../test/media/tip.png "Tip") Se a janela Propriedades não for exibida, pressione e segure **Alt** enquanto pressiona **Enter**, ou pressione **F4**.  
  
-   ![Dica](../test/media/tip.png "Tip") Para desfazer as alterações de propriedade feitas, selecione **Desfazer** do **Editar** menu ou pressione Ctrl \+ Z.  
  
-   ![Dica](../test/media/tip.png "Tip") Você pode usar o **localizar** botão na barra de editor de teste de IU codificado para abrir a ferramenta de localizar e substituir no Visual Studio. Em seguida, você pode usar o controle Find para localizar uma ação da interface do usuário no editor de teste de IU codificado. Por exemplo, você pode tentar localizar "clique em botão 'Login'." Isso pode ser útil em testes grandes. Observe que você não pode usar a funcionalidade de substituição na ferramenta de localizar e substituir no código da interface do usuário Editor de teste. Para obter mais informações, consulte Localizar controlar em [Localizando e substituindo texto](../ide/finding-and-replacing-text.md).  
  
-   ![Dica](../test/media/tip.png "Tip") Às vezes, pode ser difícil visualizar onde os controles estão localizados na interface do usuário do aplicativo em teste. Um dos recursos do que o Editor de testes de IU codificado é que você pode selecionar um controle listado no mapa do controle da interface do usuário e exibir sua localização no aplicativo em teste.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [Localizando um controle de interface do usuário do aplicativo em teste](#CodedUITestEditor_LocateUIControl) localizada mais abaixo neste tópico.  
  
-   ![Dica](../test/media/tip.png "Tip") Ele pode ser necessário expandir o controle de contêiner que contém o controle que você deseja editar.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] [Localizando um controle e seus descendentes](#CodedUITestEditor_LocateDecendants) localizada mais abaixo neste tópico.  
  
##  <a name="CodedUITestEditor_DeleteUIActions"></a> Excluir ações de interface do usuário indesejadas  
 Você pode facilmente remover ações de interface do usuário indesejadas no seu teste de IU codificado.  
  
 ![Excluir a ação de interface do usuário](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")  
  
 No **ação de interface do usuário** painel, expanda o método de teste que contém a ação de interface do usuário que você deseja excluir. Abra o menu de atalho para a ação de interface do usuário e escolha **Excluir**.  
  
##  <a name="CodedUITestEditor_SplitMethods"></a> Dividir um método de teste em dois métodos separados  
 Você pode dividir um método de teste para refinar ou modularizar as ações de interface do usuário. Por exemplo, o teste pode ter um único método de teste com ações de interface do usuário nos dois controles de contêiner. As ações de interface do usuário podem ser melhor modularizadas em dois métodos que correspondem com um contêiner.  
  
 ![Um método de teste Splt](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")  
  
 ![Dois métodos de teste](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")  
  
 No **ação de interface do usuário** painel, expanda o método de teste que você deseja dividir em dois métodos separados e selecione a ação de interface do usuário onde você deseja que o novo método de teste para começar. Ou abra o menu de atalho para a ação de interface do usuário e, em seguida, escolha **Dividir em um novo método**, ou escolha o **Dividir em um novo método** na barra de ferramentas do Editor de teste de IU codificado. O novo método de teste é exibido no painel de ações de interface do usuário. Ele contém as ações de interface do usuário a partir de ação em que você especificou a divisão.  
  
 Depois de terminar dividindo o método, salve as alterações do arquivo Uimap escolhendo **Salvar** sobre o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barra de ferramentas.  
  
 *O que mais devo saber?*  
 **Problemas importantes**  
  
-   ![Ícone de cuidado](../test/media/caution.png "caution") **Aviso:** se você dividir um método, você deve modificar qualquer código que chama o método existente para também chamar o novo método que você está prestes a criar se ainda desejar essas ações de interface do usuário incluídas. Quando você divide um método, é exibida uma caixa de diálogo do Microsoft Visual Studio. Ele avisa que você deve modificar qualquer código que chama o método existente para também chamar o novo método que você está prestes a criar. Selecione **Sim**.  
  
 **Dicas**  
  
-   ![Dica](../test/media/tip.png "Tip") Para desfazer a divisão, escolha **Desfazer** do **Editar** menu ou pressione Ctrl \+ Z.  
  
-   ![Dica](../test/media/tip.png "Tip") Você pode renomear o novo método. Selecione\-o no painel de ações de interface do usuário e escolha o **Renomear** na barra de ferramentas do Editor de teste de IU codificado.  
  
     \- ou \-  
  
     Abra o menu de atalho para o novo método de teste e escolha **Renomear**.  
  
     É exibida uma caixa de diálogo do Microsoft Visual Studio. Ele avisa que você deve modificar qualquer código que faz referência ao método. Selecione **Sim**.  
  
##  <a name="CodedUITestEditor_MoveMethods"></a> Mover um método de teste para o arquivo UIMap para facilitar a personalização  
 Se você determinar que um dos seus métodos de teste em sua interface do usuário codificado teste requer código personalizado, você deverá movê\-lo no arquivo de UIMap.cs ou Uimap. Caso contrário, seu código será substituído sempre que o teste de IU codificado é recompilado. Se você não move o método, seu código personalizado será substituído sempre que o teste for recompilado.  
  
 No **ação de interface do usuário** painel, selecione o método de teste que você deseja mover para o arquivo UIMap.cs ou Uimap para facilitar a funcionalidade de código personalizado que não será substituída quando o código de teste for recompilado. Em seguida, escolha o **Mover o código** botão na barra de ferramentas do Editor de teste de IU codificado ou abra o menu de atalho para o método de teste e escolha **Mover o código**. O método de teste é removido do arquivo Uimap e não é mais exibido no painel de ações de interface do usuário. Para editar o arquivo de teste que você moveu, abra o arquivo UIMap.cs ou o arquivo Uimap no Gerenciador de soluções.  
  
 Depois de terminar movendo o método, salve as alterações do arquivo Uimap escolhendo **Salvar** sobre o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barra de ferramentas.  
  
 *O que mais devo saber?*  
 **Problemas importantes**  
  
-   ![Ícone de cuidado](../test/media/caution.png "caution") **Aviso:** depois de mover um método, você não pode mais editá\-lo usando o Editor de teste de IU codificado. Você deve adicionar seu código personalizado e mantê\-lo usando o Editor de código. Quando você move um método, é exibida uma caixa de diálogo do Microsoft Visual Studio. Ele avisa que o método será movido do arquivo Uitest para o arquivo UIMap.cs ou Uimap arquivo e que você não será capaz de editar o método usando o Editor de teste de IU codificado. Selecione **Sim**.  
  
 **Dicas**  
  
-   ![Dica](../test/media/tip.png "Tip") Para desfazer a movimentação, selecione **Desfazer** do **Editar** menu ou pressione Ctrl \+ Z. No entanto, em seguida, remova manualmente o código do arquivo UIMap.cs ou Uimap.  
  
##  <a name="CodedUITestEditor_LocateUIControl"></a> Localizando um controle de interface do usuário do aplicativo em teste  
 Às vezes, pode ser difícil visualizar onde os controles estão localizados na interface do usuário do aplicativo em teste. Um dos recursos do que o Editor de testes de IU codificado é que você pode selecionar um controle listado no mapa do controle da interface do usuário e exibir sua localização no aplicativo em teste. Usando o **localizar o controle de interface do usuário** recurso no aplicativo em teste também pode ser usado para verificar as modificações de propriedade de pesquisa feita em um controle.  
  
 ![Localize o controle da interface do usuário](../test/media/codeduilocatecontrol.png "CodedUILocateControl")  
  
 ![Controle no aplicativo em teste](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")  
  
 No **mapa de controle de interface do usuário** painel, selecione o controle que você deseja localizar no aplicativo associado com o teste. Em seguida, abra o menu de atalho para o controle e, em seguida, escolha **localizar o controle de interface do usuário**. O aplicativo que está sendo testado, o controle é designado com uma borda azul.  
  
 *O que mais devo saber?*  
 **Problemas importantes**  
  
-   ![Ícone de cuidado](../test/media/caution.png "caution") **Aviso:** antes de localizar um controle de interface do usuário, verifique se o aplicativo associado com o teste está em execução.  
  
 **Dicas**  
  
-   ![Dica](../test/media/tip.png "Tip") Como alternativa, você pode usar o **Localizar todos os** opção para verificar se todos os controles em um contêiner podem ser corretamente localizados. Essa opção é descrita na próxima seção.  
  
##  <a name="CodedUITestEditor_LocateDecendants"></a> Localizando um controle e seus descendentes  
 Você pode verificar se todos os controles em um contêiner podem ser localizados corretamente na interface do usuário do aplicativo em teste. Isso pode ser útil para verificar alterações de propriedade de pesquisa que tenha feito no contêiner. Além disso, se houve alterações significativas na interface do usuário do aplicativo em teste, você pode validar que as propriedades de pesquisa de controle existentes ainda estão corretas.  
  
 ![Localizar todos os controles de descendentes](../test/media/codeduilocateall.png "CodedUILocateAll")  
  
 ![Todos os controles localizados](../test/media/codeduilocateall2.png "CodedUILocateAll2")  
  
 No **mapa de controle de interface do usuário** painel, selecione o controle de contêiner que você deseja localizar e exibir todos os descendentes. Em seguida, abra o menu de atalho do controle e escolha **Localizar todos os**. O controle de contêiner e todos os seus controles descendentes são marcadas no código da interface do usuário Editor de teste com uma marca de seleção verde ou um 'X' vermelho. Essas marcas permitem que você sabe se os controles foram localizados com êxito no aplicativo em teste.  
  
 *O que mais devo saber?*  
 **Problemas importantes**  
  
-   ![Ícone de cuidado](../test/media/caution.png "caution") **Aviso:** antes de localizar os controles de interface do usuário, verifique se o aplicativo associado com o teste está em execução.  
  
##  <a name="CodedUITestEditor_InsertDelay"></a> Inserir um atraso antes de uma ação de interface do usuário  
 Às vezes, convém fazer o teste aguardar para determinados eventos ocorrem, como uma janela apareça, a barra de progresso desaparecer e assim por diante. Usando o Editor de teste de IU codificado, você pode fazer isso inserindo um atraso antes de uma ação de interface do usuário. Você pode especificar quantos segundos você deseja que o atraso seja.  
  
 ![Inserir um atraso antes de uma ação de interface do usuário](../test/media/codeduidelay.png "CodedUIDelay")  
  
 ![Adicionado com 5 segundos de atraso](../test/media/codeduidealy2.png "CodedUIDealy2")  
  
 No **ação de interface do usuário** painel, expanda o método de teste que contém a ação de interface do usuário que você deseja inserir um atraso antes. Selecione a ação de interface do usuário. Em seguida, abra o menu de atalho para a ação de interface do usuário e escolha **Inserir atraso antes**. Um atraso é inserido e realçado antes da ação de interface do usuário selecionada com o seguinte texto: **Aguarde 1 segundos de atraso de usuário entre ações**. Na janela Propriedades, altere o valor para o **atraso** propriedade para o número desejado de milissegundos.  
  
 Depois de terminar inserindo o atraso, salvar as alterações no arquivo Uimap escolhendo **Salvar** sobre o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barra de ferramentas.  
  
 *O que mais devo saber?*  
 **Observações**  
  
-   ![Pré&#45;requisitos](../test/media/prereq.png "Prereq") Se você precisa garantir que um controle específico está disponível antes de uma ação de interface do usuário, considere adicionar código personalizado ao seu método de teste usando o método waitforcontrolxxx \(\) apropriado.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Fazendo testes de IU codificado aguardar eventos específicos durante a reprodução](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).  
  
 **Dicas**  
  
-   ![Dica](../test/media/tip.png "Tip") Se não for exibida a janela Propriedades, pressione e mantenha a tecla Alt enquanto pressiona Enter, ou como alternativa, pressione F4.  
  
## Recursos externos  
  
### Diretrizes  
 [Teste para entrega contínua com Visual Studio 2012 – capítulo 2: teste de unidade: Testando o interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### Perguntas frequentes  
 [Perguntas freqüentes \- 1 de testes de UI codificados](http://go.microsoft.com/fwlink/?LinkID=230576)  
  
 [Testes de UI codificados FAQ \-2](http://go.microsoft.com/fwlink/?LinkID=230578)  
  
### Fórum  
 [Visual Studio automação de testes de IU \(inclui CodedUI\)](http://go.microsoft.com/fwlink/?LinkID=224497)  
  
## Consulte também  
 [Usar automação de interface do usuário para testar código](../test/use-ui-automation-to-test-your-code.md)   
 [Criando testes de UI codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Criando um teste de interface do usuário codificado controlado por dados](../test/creating-a-data-driven-coded-ui-test.md)   
 [Gerenciando um Teste de IU Codificado a partir de uma gravação de ação existente](/devops-test-docs/test/generating-a-coded-ui-test-from-an-existing-action-recording)   
 [Instruções passo a passo: criando, editando e mantendo um teste de IU codificado](../Topic/Walkthrough:%20Creating,%20Editing%20and%20Maintaining%20a%20Coded%20UI%20Test.md)