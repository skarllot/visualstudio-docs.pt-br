---
title: "Executar aplicativos do Windows Phone no emulador | Microsoft Docs"
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
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Executar aplicativos do Windows Phone no emulador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O emulador do Windows Phone fornece um ambiente virtualizado no qual você pode depurar e testar aplicativos do Windows Phone em seu computador sem um dispositivo físico. Você pode simular eventos comuns de toque e rotação e escolher o tamanho da tela física e a resolução que deseja emular. Você também pode testar muitos recursos normalmente usados, como local, rede, notificações, sensores, acelerômetro e cartão SD opcional.  
  
 Para obter mais informações sobre os recursos que você pode testar no emulador, veja [Test app features in Windows Phone Emulator](http://msdn.microsoft.com/pt-br/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Junto com o Visual Studio, o emulador fornece um ambiente completo em que você pode criar, desenvolver, depurar e testar aplicativos do Windows Phone.  
  
##  <a name="BKMK_run"></a> Executar um aplicativo do Windows Phone no emulador  
 Enquanto você desenvolve um aplicativo do Windows Phone, pode usar o Emulador do Windows Phone para implantar e testar seu aplicativo rapidamente. Recomendamos que você teste seu aplicativo em um dispositivo Windows Phone real, mas antes de publicar seu aplicativo na Windows Phone Store. Isso permite que você tenha experiências com seu aplicativo da mesma forma que os usuários terão.  
  
 Quando você executa um aplicativo do Windows Phone pela primeira vez no Emulador do Windows Phone, podem ocorrer os seguintes eventos:  
  
1.  O emulador é iniciado.  
  
2.  O emulador carrega o sistema operacional do Windows Phone.  
  
3.  O emulador exibe a tela inicial do Windows Phone.  
  
4.  Seu aplicativo é implantado no emulador.  
  
5.  Seu aplicativo é executado no emulador.  
  
 Se o emulador selecionado já estiver em execução, seu aplicativo é implantado e iniciado no emulador em execução. Apenas uma instância de cada emulador pode executar de cada vez.  
  
> [!TIP]
>  Quando você testar seu aplicativo no emulador, deixe o emulador aberto entre as sessões de depuração, assim poderá reexecutar seu aplicativo rapidamente.  
  
###  <a name="BKMK_vs"></a> Executar o aplicativo no Visual Studio  
  
##### Para implantar e executar o aplicativo do Visual Studio  
  
1.  No Visual Studio, abra um projeto do Windows Phone.  
  
2.  Na barra de ferramentas **Padrão**, selecione uma das opções de emuladores.  
  
     ![List of Windows Phone Emulator images](../debugger/media/wp_emulator_list.png "WP\_Emulator\_list")  
  
3.  Para implantar e executar seu aplicativo com depuração, no menu **Depurar**, clique em **Iniciar Depuração** ou pressione F5.  
  
     Para implantar e executar seu aplicativo sem depuração, no menu **Depurar**, clique em **Iniciar sem Depuração** ou pressione Ctrl\+F5.  
  
     Seu aplicativo é implantado e iniciado.  
  
     Para implantar seu aplicativo sem executá\-lo, no menu **Criar**, clique em **Implantar Solução**.  
  
##### Para interromper a execução de um aplicativo  
  
-   Para interromper um aplicativo em execução, faça o seguinte:  
  
    -   No Visual Studio, no menu **Depurar**, clique em **Parar Depuração** ou pressione Shift\+F5.  
  
    -   No emulador, pressione o botão **Voltar** para sair do aplicativo. Se a página ativa do aplicativo não for a página inicial do aplicativo, pode ser necessário pressionar o botão **Voltar** mais de uma vez.  
  
     O aplicativo sai e a tela Iniciar abre. Isso encerra a sessão de depuração atual.  
  
##### Para reiniciar um aplicativo sem depuração  
  
1.  No emulador, na tela Iniciar, passe o dedo para a esquerda para exibir a lista de aplicativos.  
  
2.  Na lista de aplicativos, toque no ícone do aplicativo. O aplicativo reinicia sem depuração.  
  
##### Para desativar um aplicativo em execução  
  
1.  Antes de executar seu aplicativo, no Visual Studio, clique com o botão direito no Gerenciador de Soluções, selecione **Propriedades** para abrir o **Designer de Projeto**.  
  
2.  Se você quer que o aplicativo fique em estado do dormência quando for desativado, no **Designer de Projeto**, na página **Depurar**, deixe a caixa de seleção **Marcar como inativo após a desativação ao depurar** desmarcada. Marque a caixa de seleção se você deseja que o aplicativo fique inativo quando for desativado.  
  
3.  No menu **Depurar**, clique em **Iniciar Depuração** ou pressione F5 para executar o aplicativo.  
  
4.  No emulador, pressione o botão **Iniciar**. A tela Iniciar aparece e o aplicativo é desativado. O aplicativo entra em um estado de dormência ou é fica inativo, dependendo da configuração da caixa de seleção **Marcar como inativo após a desativação ao depurar**.  
  
##### Para reativar um dispositivo dormente ou inativo  
  
-   No emulador, pressione o botão **Voltar** para voltar ao aplicativo. Se você navegou para outras páginas ou abriu outro aplicativo, pode ser necessário pressionar o botão **Voltar** mais de uma vez para reativar o aplicativo.  
  
     A sessão de depuração é retomada. Se o depurador se soltou de seu aplicativo, pode ser necessário pressionar F5 pra retomar a sessão de depuração.  
  
###  <a name="BKMK_depltool"></a> Executar um aplicativo com a ferramenta Implantação do Aplicativo  
 Você também pode usar a ferramenta de Implantação do Aplicativo Windows Phone \(**AppDeploy.exe**\) para executar seu aplicativo no emulador. Essa ferramenta é um aplicativo independente, que é implantado quando você instala as ferramentas de desenvolvimento do Windows Phone.  
  
 Para obter mais informações, consulte [Implantar aplicativos do Windows Phone 8.1 com a ferramenta Implantação do Aplicativo](../Topic/Deploy%20Windows%20Phone%208.1%20apps%20with%20the%20Application%20Deployment%20tool.md).  
  
##  <a name="BKMK_toolbar"></a> Configurar o emulador do Windows Phone com a barra de ferramentas do emulador  
 Esta tabela mostra os botões de configuração disponíveis na barra de ferramentas do emulador.  
  
|Botões da barra de ferramentas|Opções de configuração|  
|------------------------------------|----------------------------|  
|![Input options on Windows Phone Emulator toolbar](../debugger/media/wp_emulator_.png "WP\_Emulator\_")|**Configurar entrada de um único ponto ou vários pontos**<br /><br /> Quando você habilita a entrada de vários pontos, pode clicar com o botão direito do mouse para mover os pontos de toque sem tocar na tela. E você pode clicar com o botão esquerdo para mover os dois pontos de toque simultaneamente.|  
|![Orientation on Windows Phone Emulator toolbar](../debugger/media/wp_emulator_rotation.png "WP\_Emulator\_rotation")|**Configurar a orientação do emulador**<br /><br /> Você pode alterar a orientação no Emulador do Windows Phone para uma das três orientações: retrato, paisagem à esquerda ou paisagem à direita. O tamanho do emulador não muda quando você muda a orientação.<br /><br /> Para alterar a orientação, clique no botão **Girar à esquerda** ou no botão **Girar à direita**.|  
|![Size options on Windows Phone Emulator toolbar](../debugger/media/wp_emulator_size.png "WP\_Emulator\_size")|**Configurar o tamanho do emulador**<br /><br /> Você pode mudar o tamanho do emulador na tela do computador host. O DPI \(pontos por polegada\) para o emulador é baseado no DPI do monitor host, independentemente do valor de zoom.<br /><br /> -   Para ajustar o emulador à tela, clique no botão **Ajustar à Tela**.<br />-   Para mudar a configuração de zoom, clique no botão **Zoom**. A caixa de diálogo **Zoom** é exibida. Na caixa de diálogo **Zoom**, insira um valor de zoom entre 33 e 100.|  
  
##  <a name="BKMK_buttons"></a> Use os botões de hardware simulados no emulador  
 Simule o uso dos botões de hardware de um telefone usando os botões de hardware simulados no lado direito da tela do emulador.  
  
-   Clique no botão **Ligar\/Desligar** para simular ligar e desligar a tela. Clique e segure para simular o desligamento do telefone.  
  
-   Clique nos botões **Aumentar volume** ou **Diminuir volume** para simular a alteração de volume dos alto\-falantes do telefone durante chamadas e notificações.  
  
-   O botão **Câmera** inicia o aplicativo de câmera. Você pode simular tirar uma foto ou um vídeo usando os controles no aplicativo de câmera.  
  
 A captura de tela a seguir mostra os botões de hardware simulados.  
  
1.  A imagem à esquerda exibe a tela Iniciar no emulador.  
  
2.  A imagem do meio exibe o emulador após tocar o botão **Ligar\/Desligar** para desligar a tela.  
  
3.  A imagem à direita exibe a tela do emulador após tocar o botão **Aumentar volume** para aumentar o volume.  
  
 ![Buttons on the Windows Phone emulator](../debugger/media/wp_emulator_buttons.png "WP\_Emulator\_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Usar o teclado do computador com o simulador  
 O emulador suporta mapeamento do teclado de hardware em seu computador de desenvolvimento para teclado em um Windows Phone. O comportamento das teclas é igual ao de um dispositivo Windows Phone.  
  
 Por padrão, o teclado de hardware não fica habilitado. A implementação é equivalente a um teclado deslizante que deve ser implantado antes de você poder usá\-lo. Antes de você habilitar o teclado de hardware, o emulador só aceita entrada de teclas das teclas de controle.  
  
 O emulador não suporta caracteres especiais no teclado de uma versão localizada de um computador de desenvolvimento do Windows. Para inserir caracteres especiais presentes em teclados localizados, use o SIP \(Software Input Panel\).  
  
 Para usar o teclado do computador no emulador, pressione PAGE UP chave ou a tecla PAUSE\/BREAK \(emulador do Windows 8\/8.1\) ou F4 \(Windows 10 emulador\).  
  
 Para parar de usar o teclado do computador no emulador, pressione a PAGE DOWN chave ou a tecla PAUSE\/BREAK \(emulador do Windows 8\/8.1\) ou F4 \(Windows 10 emulador\).  
  
 A tabela a seguir lista as teclas de um teclado de hardware que você pode usar para emular os botões e outros controles em um Windows Phone.  
  
|Tecla de hardware do computador|Botão de hardware do Windows Phone|Observações|  
|-------------------------------------|----------------------------------------|-----------------|  
|F1|VOLTAR|Pressionar longamente funciona como esperado.|  
|F2|INICIAR|Pressionar longamente funciona como esperado.|  
|F3|PESQUISAR||  
|F4|No emulador do Windows 10, alterna entre usar o teclado do computador local e não usando o teclado do computador local.|Não é aplicável no emulador do Windows 8\/8.1.|  
|F5|Não aplicável.||  
|F6|METADE DA CÂMERA|Um botão de câmera dedicado, que é pressionado apenas um pouco.|  
|F7|CÂMERA INTEIRA|Um botão de câmera dedicado.|  
|F8|Não aplicável.||  
|F9|AUMENTAR VOLUME||  
|F10|DIMINUIR VOLUME||  
|F11|Não aplicável.||  
|F12|LIGAR\/DESLIGAR|Pressione a tecla F12 duas vezes para habilitar a tela de bloqueio.<br /><br /> Pressionar longamente funciona como esperado.|  
|ESC|VOLTAR|Pressionar longamente funciona como esperado.|  
|PAUSE\/BREAK|Alternar teclado \(apenas no emulador do windows 8\/8.1\).|Não aplicável para o emulador do Windows 10.|  
|PAGE UP|Permite que o hardware de teclado \(apenas emulador do Windows 8\/8.1\).|Não aplicável para o emulador do Windows 10.|  
|PAGE DOWN|Desabilita o hardware de teclado \(apenas emulador do Windows 8\/8.1\).|Não aplicável para o emulador do Windows 10.|  
  
##  <a name="BKMK_checkpoints"></a> Salvar e carregar pontos de verificação personalizados  
 Salve um instantâneo do estado do emulador usando a guia **Pontos de Verificação** das **Ferramentas Adicionais** do emulador. Esse recurso é útil quando você testa seu aplicativo frequentemente com os mesmos dados e configurações.  
  
 Por exemplo, se seu aplicativo requer vários contatos, você pode criar os registros de contato uma vez e salvar um instantâneo do emulador. Do contrário, você tem de recriar o registro de contato toda vez que iniciar o emulador.  
  
-   Clique em **Novo ponto de verificação** para capturar um novo instantâneo do estado do emulador com os dados e as configurações necessários para testar seu aplicativo novamente mais tarde. Um novo ponto de verificação é adicionado à lista de **Pontos de Verificação**.  
  
     Você não pode capturar um ponto de verificação enquanto o depurador estiver anexado ao emulador.  
  
-   Selecione um ponto de verificação na lista de **Pontos de Verificação** para exibir informações sobre o ponto de verificação.  
  
-   Escolha o botão de opção na coluna **Padrão** para tornar um ponto de verificação salvo como ponto de verificação padrão para o emulador ativo.  
  
-   Clique em **Restaurar** para reiniciar o sistema operacional do Windows Phone no emulador e carregar o instantâneo selecionado.  
  
-   Clique em **Excluir** para excluir um instantâneo que você não precisa mais.  
  
 A imagem original do emulador sempre aparece como o primeiro item na lista de **Pontos de verificação** e não pode ser alterada ou excluída. No entanto, você pode selecionar um instantâneo diferente como imagem padrão do emulador.  
  
 ![Checkpoints tab of the Windows Phone Emulator](../debugger/media/wp_emulator_checkpoints.png "WP\_Emulator\_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Capturar capturas de tela no emulador  
 Você pode criar capturas de tela de seus aplicativos do Windows Phone usando a ferramenta de captura de tela a partir da janela Ferramentas adicionais. A ferramenta cria arquivos PNG que correspondem à resolução do emulador em execução.  
  
 ![Screenshots from the Windows Phone Emulator](~/debugger/media/wp_emulator_screenshots.png "WP\_Emulator\_screenshots")  
  
#### Para criar uma captura de tela do aplicativo usando a ferramenta de captura de tela interna do emulador  
  
1.  Para otimizar a qualidade de suas capturas de tela, defina o nível de zoom do emulador para 100%. Quanto mais alto você definir o nível de zoom, melhor será a qualidade da captura de tela.  
  
2.  Inicie seu aplicativo no emulador.  
  
3.  Na barra de ferramentas do emulador, clique no botão expandir para abrir a janela **Ferramentas Adicionais**.  
  
4.  Clique na guia **Captura de Tela**.  
  
5.  Quando o aplicativo estiver pronto, clique no botão **Capturar**.  
  
     A captura de tela aparece no espaço de trabalho.  
  
6.  Clique no botão **Salvar** para abrir a caixa de diálogo **Salvar como**.  
  
7.  Escolha o local e o **Nome do arquivo** que você deseja e clique em **Salvar**.  
  
8.  Como opção, navegue para outras páginas em seu aplicativo para capturar telas adicionais.  
  
9. Inicie o emulador com uma resolução de tela diferente para capturar as mesmas telas com uma resolução diferente. Se você executou seu aplicativo ao depurar, é necessário parar a depuração antes de poder executá\-lo novamente em outro emulador.  
  
 Desabilite os contadores de taxa de quadros na tela do emulador antes de capturar telas que serão enviadas à Windows Phone Store.  
  
#### Para desabilitar os contadores de taxa de quadros no emulador antes de capturar telas  
  
-   Especifique uma criação de versão no Visual Studio. Após especificar uma criação de versão, inicie seu aplicativo selecionando o link **Implantar *\[nome do aplicativo\]*** no menu **Criar**.  
  
-   Como alternativa, você pode comentar na linha de código do arquivo app.xaml.cs ou app.xaml.vb que define o valor de `EnableFrameRateCounter` para `true`.