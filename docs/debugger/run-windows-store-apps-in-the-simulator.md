---
title: "Executar aplicativos da Windows Store no simulador | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 42
caps.handback.revision: 42
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Executar aplicativos da Windows Store no simulador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O simulador do Visual Studio para aplicativos da Windows Store é um aplicativo da área de trabalho que simula um aplicativo da Windows Store. Você pode executar aplicativos e simular eventos de rotação e toque comum no computador de desenvolvimento. Você também pode escolher o tamanho da tela física e a resolução que você deseja emular e simular propriedades de conexão de rede.  
  
 O simulator oferece um ambiente no qual você pode criar, desenvolver, depurar e testar aplicativos da Windows Store. No entanto, antes de publicar um aplicativo na Windows Store, convém testá\-lo em um dispositivo real.  
  
 O simulador do Visual Studio para aplicativos da Windows Store não é executado em um ambiente isolado na máquina local. Portanto, os erros que ocorrem no simulador, como um erro não recuperável geral do sistema, também podem afetar o computador inteiro.  
  
 Veja [Executar aplicativos do Windows Phone no emulador](../debugger/run-windows-phone-apps-in-the-emulator.md) para obter informações do Windows Phone.  
  
> [!IMPORTANT]
>  Simulador do Visual Studio 2015 não inclui o botão de localização geográfica. Isso ocorre porque o simulador do Windows 10 não inclui a simulação de localização geográfica. Se você precisar fazer esse tipo de simulação, você pode usar o simulador do Visual Studio 2013 no Windows 8.1 ou sistemas operacionais anteriores.  
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Definir o simulador como o destino  
 Para executar seu aplicativo da Windows Store no simulador, selecione **Simulador** na lista suspensa ao lado do botão **Iniciar Depuração** na barra de ferramentas **Padrão** do depurador.  
  
 ![Em execução no simulador](~/docs/debugger/media/vsrun_f5_simulator.png "VSRUN\_F5\_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Escolher um modo de interação  
 Você pode escolher os seguintes modos de interação  
  
-   ![Botão de modo](~/docs/debugger/media/simulator_mousemodebtn.png "SIMULATOR\_MouseModeBtn") Modo de mouse: define o modo de interação para gestos de mouse. Esses gestos incluem cliques, cliques duplos e arrastos.  
  
-   ![Toque emulação botão Iniciar](~/docs/debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR\_StartTouchEmulationBtn") Iniciar a emulação de toque: define o modo de interação para gestos de um único dedo. Os eventos desse tipo incluem tocar, arrastar e passar o dedo.  
  
     ![Simulator one finger target](../debugger/media/simulator_onefinger.png "SIMULATOR\_OneFinger") O ícone de destino único indica o local de eventos no simulador. Use o mouse para posicionar o ponteiro.  
  
     ![One finger touch target](../debugger/media/simulator_onefingerengaged.png "SIMULATOR\_OneFingerEngaged") Pressione o botão esquerdo do mouse para ativar o modo de toque. Por exemplo, clique no botão para simular um gesto de tocar, ou pressione e segure o botão enquanto você arrasta ou passa o dedo.  
  
## Aperto e zoom  
 Defina o modo de interação como sendo gestos de aperto e zoom com dois dedos.  
  
-   ![Siimulator two finger target](~/docs/debugger/media/simulator_twofinger.png "SIMULATOR\_TwoFinger")  
  
     O ícone de alvo duplo indica o local de dois dedos na tela do dispositivo.  
  
    -   Mova o mouse para posicionar os ícones sobre o objeto na tela do dispositivo.  
  
    -   Gire a roda do mouse para trás ou para a frente a fim de alterar a distância simulada dos dois dedos antes de apertar ou aplicar zoom.  
  
-   -   ![Pinch, zoom, and rotate targets](../debugger/media/simulator_twofingerengaged.png "SIMULATOR\_TwoFingerEngaged")  
  
         Pressione o botão esquerdo e gire a roda para trás \(na sua direção\) a fim de ampliar a exibição \(aperto\).  
  
    -   Pressione o botão esquerdo e gire a roda do mouse para a frente \(afastada de você\) a fim de reduzir a exibição \(zoom\).  
  
## Rotação de objeto  
 O **emulação de toque girar** botão define o modo de interação para gestos de rotação usando dois dedos.  
  
-   -   Mova o mouse para posicionar os ícones sobre o objeto na tela do dispositivo.  
  
    -   Gire a roda do mouse para trás ou para frente para alterar a orientação simulada dos dois dedos antes de girar o objeto.  
  
-   -   Pressione o botão esquerdo e gire a roda para trás \(na sua direção\) a fim de girar o objeto no sentido anti\-horário. Conforme você gira a roda do mouse, um dos dois ícones de alvo gira em torno do outro para indicar o tamanho relativo da rotação.  
  
    -   Pressione o botão esquerdo e gire a roda do mouse para a frente \(afastada de você\) a fim de girar o objeto no sentido horário.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Habilitar ou desabilitar o modo Sempre visível  
 Você pode configurar a janela do simulador para ficar sempre por cima das outras janelas. O **janela superior alternância** botão habilita ou desabilita o **sempre visível** modo da janela do simulador.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Alterar a orientação do dispositivo  
 Você pode alternar a orientação do dispositivo entre retrato e paisagem girando o simulador 90 graus em qualquer direção.  
  
> [!NOTE]
>  O simulator não respeitam [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) propriedade de um projeto. Por exemplo, se o projeto define a orientação como `Landscape` e você gira o simulador até a orientação retrato, a imagem de exibição do simulador também é girada e redimensionada. Teste essas configurações em um dispositivo real.  
  
> [!NOTE]
>  Se você gira o simulador de modo que uma borda dele fica maior do que a tela em que ele é exibido, o simulador é automaticamente redimensionado para caber na tela. O simulador não é redimensionado para o tamanho original se você o gira novamente.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Alterar o tamanho e a resolução de tela simulados  
 Para alterar o tamanho da tela simulados e a resolução, escolha o **Alterar resolução** botão na paleta e escolha um novo tamanho e resolução da lista.  
  
 O tamanho e a resolução da tela são listados como *Largura da tela em polegadas, largura em pixel X altura em pixel*. Observe que tanto o tamanho como a resolução da tela são simulados. As coordenadas de local no simulador são convertidas nas coordenadas do tamanho e da resolução do dispositivo selecionado.  
  
> [!NOTE]
>  Você pode salvar versões dimensionadas de imagens de bitmap em seu aplicativo, e o Windows carregará a imagem correta para a escala atual. Para obter mais informações, consulte [101 de Design responsivo](https://msdn.microsoft.com/en-us/library/windows/apps/dn958435.aspx). No entanto, se você alterar a resolução do simulador de modo que o Windows selecione uma imagem diferente para ajustar à resolução, será preciso parar e reiniciar a sessão de depuração para exibir a nova imagem.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Fazer uma captura de tela do aplicativo para envio ao Windows Store  
 Quando você envia um aplicativo da Windows store, você deve incluir capturas de tela do aplicativo.  
  
> [!NOTE]
>  A captura de tela é salva na resolução atual do simulador. Para alterar a resolução, escolha o botão **Alterar Resolução**.  
  
-   Para criar capturas de tela do aplicativo a partir do simulador, escolha o botão **Capturar tela na área de transferência**.  
  
-   Para definir o local onde se encontram as capturas de tela, escolha o **configurações de captura de tela** botão e escolha o local no menu de atalho.  
  
     ![Screenshot settings context menu](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR\_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simular propriedades de conexão de rede  
 Você pode ajudar os usuários de seu aplicativo a gerenciar o custo de conexões de rede limitadas mantendo a percepção do custo da conexão de rede ou as alterações de status do plano de dados e habilitando o aplicativo para usar essas informações para evitar a cobrança de custos adicionais para roaming ou exceder um limite especificado de transferência de dados. O [Windows.Networking.Connectivity](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.aspx) APIs permite que você responda às [NetworkStatusChanged](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) e [TriggerType](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) eventos que entrarem. Consulte [início rápido: as restrições de custo do gerenciamento de rede limitada](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Para depurar ou testar seu código com reconhecimento de custo da rede, o simulator pode simular propriedades de uma rede que são expostos por meio de [ConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) objeto retornado por [GetInternetConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx)...  
  
 Para simular propriedades de rede:  
  
1.  Na barra de ferramentas do simulador, escolha o **alterar propriedades de rede** botão.  
  
2.  Sobre o **definir propriedades de rede** caixa de diálogo, selecione **uso simulado propriedades de rede**.  
  
     Desmarque a caixa de seleção para remover a simulação e retornar às propriedades de rede da interface atualmente conectada.  
  
3.  Digite um **Nome de Perfil** para a rede simulada. É recomendável usar um nome exclusivo que você pode usar para identificar a simulação no [ProfileName](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) propriedade o [ConnectionProfile](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) objeto.  
  
4.  Selecione o [NetworkCostType](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) valor para o perfil do **tipo de custo de rede** lista.  
  
5.  Do **sinalizador de Status de limite de dados** lista, você pode definir o [ApproachingDataLimit](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) propriedade ou o [OverDataLimit](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)propriedade como true, ou você pode escolher **sob o limite de dados** para definir os dois valores como false.  
  
6.  Do **Roaming estado** lista, defina o [Roaming](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) propriedade.  
  
7.  Escolha **definir propriedades** para simular as propriedades de rede Disparando um primeiro plano [NetworkStatusChanged](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) eventos e um plano de fundo [SystemTrigger](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) do tipo **NetworkStateChange**.  
  
 **Mais informações sobre como gerenciar conexões de rede**  
  
 [Início rápido: Gerenciando monitorados restrições de custo de rede](http://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
 [Exemplo de informações de rede](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
 [Analisar o uso de energia](../profiling/analyze-energy-use-in-store-apps.md)  
  
 [Windows.Networking.Connectivity](https://msdn.microsoft.com/en-us/library/windows/apps/windows.networking.connectivity.aspx)  
  
 [Como responder a eventos do sistema com tarefas em segundo plano](http://msdn.microsoft.com/pt-br/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
 [Como disparar suspender, continuar e eventos em aplicativos da Windows Store do plano de fundo](http://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Navegar no simulador com o teclado  
 Você pode navegar a barra de ferramentas do simulador pressionando **CTRL \+ ALT \+ seta acima** para alternar o foco da janela simulator na barra de ferramentas do simulador. Use a **seta para cima** e a **seta para baixo** para se movimentar entre os botões da barra de ferramentas.  
  
 Você pode desligar o simulator pressionando **CTRL \+ ALT \+ F4**.  
  
## Consulte também  
 [Executar aplicativos pelo Visual Studio](../debugger/run-store-apps-from-visual-studio.md)