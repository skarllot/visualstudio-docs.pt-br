---
title: "Notificações e progresso para o Visual Studio | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1f7823754601161200edafdce998ebe9aeab2723
ms.lasthandoff: 02/22/2017

---
# <a name="notifications-and-progress-for-visual-studio"></a>Notificações e o progresso do Visual Studio
##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a>Sistemas de notificação  
  
### <a name="overview"></a>Visão Geral  
 Há várias maneiras para informar ao usuário que está acontecendo no Visual Studio sobre suas tarefas de desenvolvimento de software.  
  
 Ao implementar qualquer tipo de notificação:  
  
-   **Mantenha o número de notificações para o mínimo** número efetivo. Mensagens de notificação devem aplicar a maioria dos usuários do Visual Studio ou a usuários de uma área de recurso/recurso específico. O uso excessivo de notificações pode sidetrack o usuário ou ser reduzido percebida facilidade de uso do sistema.  
  
-   **Certifique-se de que você está apresentando mensagens e práticas** que o usuário pode usar para invocar o contexto apropriado para fazer escolhas mais complexas e necessária mais ação.  
  
-   **Apresente mensagens síncronas e assíncronas adequadamente.** Notificações síncronas indicam que algo precisa de atenção imediata, como quando um serviço web falha ou um código de exceção é lançada. O usuário deve ser informado sobre essas situações imediatamente de forma que solicita sua entrada, como em uma caixa de diálogo modal. Notificações assíncronas são aquelas que o usuário deve saber, mas não ser necessário para agir imediatamente, como quando uma operação de compilação for concluída ou quando uma conclusão da implantação de sites. Essas mensagens devem ser mais ambiente e não interrompem o fluxo de tarefas do usuário.  
  
-   **Use as caixas de diálogo modais somente quando necessário para impedir que o usuário executar uma ação adicional** antes de confirmar a mensagem ou tomar uma decisão apresentada na caixa de diálogo.  
  
-   **Remova notificações de ambiente quando eles não são mais válidos.** Requer que o usuário descartar uma notificação se já executou a ação para resolver o problema que foram notificados sobre eles.  
  
-   **Lembre-se de que as notificações podem levar a correlações falsas.** Os usuários podem acreditar que um ou mais de suas ações acionou uma notificação quando na verdade não havia nenhuma relação causal. Seja clara na mensagem de notificação sobre o contexto, o gatilho e a fonte da notificação.  
  
### <a name="choosing-the-right-method"></a>Escolha do método certo  
 Use esta tabela para ajudá-lo na escolha do método certo para notificar o usuário da mensagem.  
  
|Método|Uso|Não use|  
|------------|---------|----------------|  
|[Caixas de diálogo de mensagem de erro modal](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Use quando uma resposta do usuário é necessária antes de continuar.|Não use quando não é necessário para impedir que o usuário e interromper o fluxo. Evite usar caixas de diálogo modais se é possível mostrar a mensagem de outra maneira menos intrusiva.|  
|[Barra de status do IDE](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Use quando houver ambiente informações textuais sobre o status de um processo.|Não use sozinho. Melhor usada em conjunto com outro mecanismo de comentários.|  
|[Barra de informações inserida](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Em uma janela de ferramenta ou janela de documento, use a notificação de progresso, estado de erro, resultados e/ou informações acionáveis.|Não use se as informações não são relevantes para o local onde a barra de informações é colocada.<br /><br /> Não use fora de uma janela de ferramenta do documento.|  
|[Alterações de cursor do mouse](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Pode ser usado para notificar que um processo está acontecendo. Também é usado para notificar que há uma alteração de estado do mouse, como quando arrastar/soltar está em andamento ou que o cursor do mouse em um determinado modo, como o modo de desenho.|Não use para alterações de progresso curto ou se fluttering do cursor é provável (por exemplo, quando vinculados a partes de um processo em execução mais longo em vez de todo o processo).|  
|[Indicadores de progresso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|Usar quando for necessário para relatar o progresso (determinado ou indeterminado). Há uma variedade de tipos de indicador de progresso e de uso específico para cada. Consulte [indicadores de progresso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||  
|[Janela do Visual Studio notificações](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|A janela de notificações não é extensível publicamente. No entanto, ele é usado para comunicar-se um intervalo de mensagens sobre o Visual Studio, incluindo problemas críticos com sua licença e informativas notificações de atualizações para o Visual Studio ou aos pacotes.|Não use para outros tipos de notificações.|  
|[Lista de erros](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Quando o problema está diretamente relacionado a solução aberta no momento do usuário, há um problema (erro/aviso/informação), que podem ser necessárias executar a ação no código.<br /><br /> Isso inclui, por exemplo:<br /><br /> -Mensagens do compilador (erro/aviso/informação)<br /><br /> -Mensagens de diagnóstico/Analyzer código sobre o código<br /><br /> -Mensagens de compilação<br /><br /> Pode ser apropriada para problemas relacionados aos arquivos de projeto ou solução, mas considere uma indicação do Solution Explorer primeiro.|Não use para itens que não têm nenhuma relação com o código do usuário solução aberta.|  
|Notificações do Editor: lâmpada|Use quando tiver uma correção disponível para solucionar um problema que existe no arquivo aberto.<br /><br /> Observe que a lâmpada também deve ser usado para hospedar as ações rápidas que são executadas em código do usuário sob demanda, como refatorações, mas nesse caso, não será exibido "estilo de notificação".|Não use para itens que não têm nenhuma relação com o arquivo aberto.|  
|Notificações do Editor: rabiscos|Use para alertar o usuário para um problema com um intervalo específico de seu código aberto (por exemplo, um rabisco vermelho para erros).|Não use para itens que não estão relacionados a uma extensão específica do código aberto.|  
|[Barras de status incorporados](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Use para fornecer status relacionadas ao conteúdo ou processo no contexto de uma janela de ferramenta específica, documento ou janela de diálogo.|Não use para notificações gerais do produto, processos ou itens que não têm nenhuma relação com o conteúdo dentro da janela específica.|  
|[Notificações da bandeja do Windows](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Use para notificações para processos fora do processo de superfície ou complementar aplicativos.|Não use para notificações que são relevantes para o IDE.|  
|[Bolhas de notificação](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Use para notificar um processo remoto ou alterar **fora de** do IDE.|Não use como um meio para notificar o usuário dos processos **em** IDE.|  
  
### <a name="notification-methods"></a>Métodos de notificação  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Caixas de diálogo de mensagem de erro modal  
 Uma caixa de diálogo de mensagem de erro modal é usada para exibir uma mensagem de erro que exige confirmação ou ação do usuário.  
  
 ![Mensagem de erro modal](~/docs/extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "01_ModalErrorMessage&0901;")  
  
 **Uma caixa de diálogo de mensagem de erro modal alertando o usuário de uma cadeia de caracteres de conexão inválido para um banco de dados**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>Barra de status do IDE  
 A probabilidade de que os usuários percebem o texto da barra de status se correlaciona com sua experiência geral e experiência específica com a plataforma Windows. A base de clientes do Visual Studio tende a ter experiência em ambas as áreas, embora os usuários de Windows ainda mais experientes poderá perder as alterações na barra de status. Portanto, a barra de status é usada para fins informativos ou como uma indicação redundante melhor para as informações apresentadas em outro lugar. Qualquer tipo de informações importantes que o usuário deve resolver imediatamente deve ser fornecido em uma caixa de diálogo ou na janela da ferramenta de notificações.  
  
 A barra de status do Visual Studio foi projetada para permitir vários tipos de informação a ser exibida. Ele é dividido em regiões para comentários, designer, barra de progresso, animação e cliente.  
  
 A região de comentários e a região designer são sempre visíveis. A barra de progresso e a animação regiões sempre são dinâmicos e com base no contexto do usuário. A região designer tem uma largura estática determinada pelo tamanho da cadeia de caracteres que é recebida de um recurso que acompanha este artigo para a mensagem de texto. Isso permite que a localização redimensionar a largura sem exigir uma alteração de código. Para o inglês, a largura dessa cadeia de caracteres é aproximadamente 220 pixels. A região designer irá se comportar normalmente e a região de comentários de absorver o espaço restante.  
  
 A barra de status também é colorida para adicionar interesse visual e funcional valor comunicando-se várias alterações de estado IDE, como quando o IDE está no modo de depuração.  
  
 ![Status IDE alterações de cor da barra](~/docs/extensibility/ux-guidelines/media/0901-02_idestatusbar.png "02_IDEStatusBar&0901;")  
  
 **Cores da barra de status IDE**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Barra de informações inserida  
 Uma barra de informações pode ser usada na parte superior de uma janela de documento ou janela de ferramenta para informar ao usuário de um estado ou condição. Ele também pode oferecer comandos para que o usuário possa ter uma maneira facilmente agir. Na barra de informações é um controle padrão do shell. Evite criar suas próprias, que atuará e exibida inconsistente com outras pessoas no IDE. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) para obter detalhes de implementação e diretrizes de uso.  
  
 ![Incorporado a barra de informações](~/docs/extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "03_EmbeddedInfobar&0901;")  
  
 **Uma barra de informações inseridas em uma janela de documento, alertando o usuário que o IDE está no modo de depuração histórico e o editor não responderá da mesma maneira como faz no modo de depuração padrão.**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Alterações de cursor do mouse  
 Ao alterar o cursor do mouse, use cores que estão vinculadas ao serviço VSColor e já estão associados com o cursor. Alterações de cursor podem ser usadas para indicar uma operação em andamento, bem como visitas regiões em que o usuário está passando por um destino que pode ser arrastado, solta ou usado para selecionar um objeto.  
  
 Use o cursor do mouse ocupado/espera somente quando todo o tempo da CPU disponível deve ser reservado para uma operação, impedindo que o usuário expressar qualquer entrada adicional. Na maioria dos casos com aplicativos bem escritos que usam multithreading, vezes quando os usuários são impedidos de fazer outras operações devem ser incomum.  
  
 Tenha em mente que as alterações de cursor são úteis como uma indicação redundante para obter informações apresentado em outro lugar. Não confie em uma alteração de cursor como a única maneira de se comunicar com o usuário, especialmente ao tentar transmitir algo que é essencial que o usuário deve atender.  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>Indicadores de progresso  
 Indicadores de progresso são importantes para fornecer o feedback do usuário durante os processos que levam mais de alguns segundos para concluir. Indicadores de progresso podem ser mostradas no local (quase o ponto de partida da ação em andamento), em uma barra de status incorporada, em uma caixa de diálogo modal ou na barra de status do Visual Studio. Siga as orientações [indicadores de progresso](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) sobre seu uso e implementação.  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Janela do Visual Studio notificações  
 A janela de notificações do Visual Studio notifica os desenvolvedores sobre licenciamento, ambiente (Visual Studio), extensões e atualizações. Os usuários podem descartar notificações individuais ou podem optar por ignorar determinados tipos de notificações. A lista de notificações ignoradas é gerenciada em uma **Ferramentas > opções** página.  
  
 A janela de notificações não é atualmente extensível.  
  
 ![Janela do Visual Studio notificações](~/docs/extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "06_VSNotificationsWindow&0901;")  
  
 **Janela de ferramentas do Visual Studio notificações**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a>Lista de erros  
 Uma notificação dentro da lista de erro indicam erros e avisos que ocorreram durante a compilação e ou processo de compilação e permite que o usuário navegue em código para esse erro de código específico.  
  
 ![Lista de erros](~/docs/extensibility/ux-guidelines/media/0901-08_errorlist.png "08_ErrorList&0901;")  
  
 **Lista de erros no Visual Studio**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Barras de status incorporados  
 Como a barra de status do IDE é dinâmica, com seu contexto de região de cliente definido como a janela do documento ativo e informações de atualização no contexto do usuário e/ou respostas de sistema, é difícil a manter uma exibição contínua das informações de status sobre processos assíncronos longo prazo. Por exemplo, a barra de status do IDE não é apropriada para as notificações de resultados de teste para várias execuções e/ou seleção de item podem ser acionados imediatamente. É importante manter essas informações de status no contexto da janela do documento ou uma ferramenta onde o usuário faz uma seleção ou inicia um processo.  
  
 ![Barra de status incorporada](~/docs/extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "09_EmbeddedStatusBar&0901;")  
  
 **Barra de status incorporada no Visual Studio**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Notificações da bandeja do Windows  
 Área de notificação está próximo do sistema Windows relógio da barra de tarefas do Windows. Muitos utilitários e componentes de software fornecem ícones nessa área, para que o usuário possa obter um menu de contexto para tarefas de todo o sistema, como alterar a resolução da tela ou obter atualizações de software.  
  
 Notificações de nível de ambiente devem ser reproduzidas no hub de notificações do Visual Studio, não a área de notificação do Windows.  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bolhas de notificação  
 Bolhas de notificação podem aparecer como informação em um editor/designer ou como parte da área de notificação do Windows. O usuário percebe esses bolhas como problemas que possam resolver mais tarde, que é um benefício para notificações críticas. Bolhas são inadequadas para obter informações importantes que o usuário deve resolver imediatamente. Se você usar balões de notificação no Visual Studio, execute o [diretrizes de área de trabalho do Windows para bolhas de notificação](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx).  
  
 ![Balão de notificação](~/docs/extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "07_NotificationBubbles&0901;")  
  
 **Balão de notificação na área de notificação do Windows usada para o Visual Studio**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>Indicadores de progresso  
  
### <a name="overview"></a>Visão Geral  
 Indicadores de progresso são uma parte importante de um sistema de notificação para apresentar os comentários do usuário. Eles informam o usuário quando os processos e as operações serão concluída. Tipos de indicador familiar incluem barras de progresso, girando cursores e ícones animados. O tipo e o posicionamento de um indicador de progresso depende do contexto, incluindo o que está sendo relatado e quanto tempo o processo ou operação levará para ser concluída.  
  
#### <a name="factors"></a>Fatores  
 Para determinar qual tipo de indicador é apropriado, você precisa determinar os fatores a seguir.  
  
1.  **Intervalo:** período de tempo em que a operação será necessário  
  
2.  **Modalidade:** se a operação está restrita ao ambiente (bloqueios a interface do usuário até que o processo for concluído)  
  
3.  **Persistente/transitório:** se o resultado final do andamento deve ser relatado e/ou podem ser exibidos em um momento posterior  
  
4.  **Determinada/indeterminado:** se a hora de término da operação e o progresso podem ser calculados  
  
5.  **Local do elemento gráfico/Textual:** se o andamento ou o processo é capturada embutidas, no corpo de uma mensagem ou um controle específico, como o controle de árvore  
  
6.  **Proximidade:** se o progresso deve estar na proximidade com a interface do usuário que está relacionado a. (Por exemplo, pode ser na barra de status, que pode ser bem longe, ou precisa ser perto do botão que iniciou o processo?)  
  
#### <a name="determinate-progress"></a>Progresso determinada  
  
|Tipo de andamento|Quando e como usar|Observações|  
|-------------------|-------------------------|-----------|  
|Barra de progresso (determinada)|Duração de esperada >&5; segundos.<br /><br /> Pode incluir uma descrição textual de detalhes do processo.|**Não** incorporar a animação de texto.|  
|Barra de informações|Mensagem associada a interface de usuário contextual. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> Pode incluir uma descrição textual de detalhes do processo.|**Não** usar várias infobars quando você precisa indicar vários processos. Use as barras de progresso empilhadas.|  
|Janela Saída|Notificação transitória: processo no nível do aplicativo que o usuário deseja **examine** detalhes de após a conclusão.|**Não** usar se o usuário precisará fazer referência a dados posteriormente.|  
|Arquivo de log|Combinado com notificação intransient em casos quando é importante **salvar** detalhes após a conclusão.||  
|Barra de status|Notificação transitória: processo no nível do aplicativo que o usuário será **não precisa** detalhes de após a conclusão.<br /><br /> Inclui uma barra de progresso incorporado.<br /><br /> Pode incluir uma descrição textual de detalhes do processo.||  
  
#### <a name="indeterminate-progress"></a>Andamento indeterminada  
  
|Tipo de andamento|Quando e como usar|Observações|  
|-------------------|-------------------------|-----------|  
|Barra de progresso (indeterminada)|Duração de esperada >&5; segundos.<br /><br /> Pode incluir uma descrição textual de detalhes do processo.|**Não** incorporar a animação de texto.|  
|ANTS (animados pontos horizontais)|Ida e volta ao servidor.<br /><br /> Colocado próximo ponto de contexto na parte superior do contêiner pai.|**Não** usar se não geradas pelo contêiner inteiro.|  
|Controle giratório (anel de progresso)|Processo associado com a interface de usuário contextual, ou onde o espaço é uma consideração.<br /><br /> Pode incluir uma descrição textual de detalhes do processo.||  
|Barra de informações|Mensagem associada a interface de usuário contextual. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**Não** usar várias infobars quando você precisa indicar vários processos. Use as barras de progresso empilhadas.|  
|Janela Saída|Notificação transitória: processo no nível do aplicativo que o usuário desejará **examine** detalhes de após a conclusão.|**Não** usar para obter informações que precisa persistem entre sessões.|  
|Arquivo de log|Combinado com notificação intransient em casos quando é importante **salvar** detalhes após a conclusão.||  
|Barra de status|Notificação transitória: processo no nível do aplicativo que o usuário será **não precisa** detalhes de após a conclusão.<br /><br /> Inclui a barra de progresso incorporado.<br /><br /> Pode incluir uma descrição textual de detalhes do processo.||  
  
### <a name="progress-indicator-types"></a>Tipos de indicador de andamento  
  
#### <a name="progress-bars"></a>Barras de progresso  
  
##### <a name="indeterminate"></a>Indeterminado  
 ![Barra de progresso indeterminado](~/docs/extensibility/ux-guidelines/media/0901-04_indeterminate.png "04_Indeterminate&0901;")  
  
 **Barra de progresso indeterminado**  
  
 "Indeterminado" significa que o progresso geral de uma operação ou processo não pode ser determinado. Use as barras de progresso indeterminado para operações que exigem uma quantidade ilimitada de tempo ou que um número desconhecido de objetos de acesso. Use uma descrição textual para acompanhar o que está acontecendo. Use tempos limite para fornecer limites de operações com base no tempo. Barras de progresso indeterminado usam animações para mostrar que o progresso está sendo feita, mas não fornecer nenhuma outra informação. Não escolha uma barra de progresso indeterminado com base apenas nos possíveis falta de precisão sozinho.  
  
##### <a name="determinate"></a>Determinada  
 ![Barra de progresso determinada](~/docs/extensibility/ux-guidelines/media/0901-05_determinate.png "05_Determinate&0901;")  
  
 **Barra de progresso determinada**  
  
 "Determinada" significa que um processo ou operação requer uma quantidade limitada de tempo, mesmo que o período de tempo não pode ser previsto com precisão. Indicam claramente a conclusão. Não deixe que uma barra de progresso vá até 100 por cento, a menos que a operação foi concluída. Animação da barra de progresso determinada move esquerda para a direita de 0 a 100%.  
  
 Nunca mova o indicador de progresso com versões anteriores durante uma operação. A barra deve seguir em frente constantemente quando a operação é iniciada e atingir 100% quando ele termina. O ponto da barra de progresso é dar ao usuário uma ideia de quanto tempo leva de toda a operação, independentemente de quantas etapas envolvidas.  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>Simultâneas reporting (barras empilhadas progresso)  
 Se uma operação levará um longo tempo – talvez vários minutos, em seguida, duas barras de andamento podem ser usado, um que mostra o andamento geral de uma operação e outro para a progressão da etapa atual. Por exemplo, se um programa de instalação está copiando os arquivos muitos, uma barra de progresso pode ser usada para indicar quanto tempo leva para todo o processo enquanto um segundo pode indicar qual é a porcentagem do arquivo ou diretório está sendo copiado. Não relatar mais de cinco processos usando barras de progresso empilhadas ou operações simultâneas. Se você tiver mais de cinco processos para relatório ou operações simultâneas, use uma caixa de diálogo modal com um botão Cancelar e relatório de detalhes do progresso na janela Saída.  
  
##### <a name="textual-descriptions"></a>Descrições  
 Use uma descrição textual para acompanhar o que está acontecendo e o tempo estimado para conclusão. Se for impossível determinar quanto tempo levará uma operação, uma opção melhor para fazer comentários pode ser um ícone animado em vez de uma barra de progresso.  
  
 O Visual Studio fornece uma barra de progresso padrão na barra de status que pode ser usada por qualquer produto integrado ao Visual Studio. Para descrições do que está acontecendo enquanto a barra de progresso é animada, o texto da barra de status pode ser atualizado.  
  
#### <a name="other-progress-indicators"></a>Outros indicadores de progresso  
  
##### <a name="ants-animated-horizontal-dots"></a>ANTS (animados pontos horizontais)  
 ![Progresso ants](~/docs/extensibility/ux-guidelines/media/0903-01_ants.png "0903&01;_Ants")  
  
 "Ants" animados pontos horizontais, fornecer uma referência visual para um processo do servidor de ida e volta indeterminado.  
  
##### <a name="spinner-progress-ring"></a>Controle giratório (anel de progresso)  
 ![Controle giratório de progresso](~/docs/extensibility/ux-guidelines/media/0903-02_spinner.png "0903&02;_Spinner")  
  
 O controle giratório (também conhecido como um "anel de progresso") é um indicador de progresso indeterminado usado principalmente em relação à interface de usuário contextual. Exiba um controle giratório em proximidade com seu conteúdo relacionado, como um cabeçalho de categoria textual, mensagens ou controle.  
  
##### <a name="cursor-feedback"></a>Comentários de cursor  
 Para operações que levar entre 2-7 segundos, fornece comentários de cursor. Normalmente, isso significa usar o cursor de espera fornecido pelo sistema operacional. Para obter orientação, consulte o artigo do MSDN [Cursors.Wait propriedade](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).  
  
#### <a name="progress-indicator-locations"></a>Locais de indicador de andamento  
  
##### <a name="status-bar"></a>Barra de status  
 A barra de status fornece um local para exibir informações úteis e mensagens para o usuário sem interromper o trabalho do usuário de seu aplicativo. Normalmente, exibida na parte inferior de uma janela, status de progresso será um painel de dica de ferramenta que inclui uma mensagem sobre a medida de progresso em combinação com um indicador de barra de progresso.  
  
 ![Barra de status com a barra de progresso](~/docs/extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903&03;_StatusBarProgressBar")  
  
 **Barra de status com a barra de progresso**  
  
 ![Barra de status com mensagens](~/docs/extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903&04;_StatusBarMessage")  
  
 **Barra de status com descrição textual**  
  
##### <a name="infobar"></a>Barra de informações  
 Semelhante à barra de status, a barra de informações fornece notificação contextual e mensagens, que também pode ser emparelhado com indicadores de progresso indeterminado, como o controle giratório ou barra de progresso. A barra de informações não deve fornecer a indicação de progresso determinada ou andamento nível granular. Consulte [Infobars](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).  
  
 ![Barra de informações com a barra de progresso e mensagens](~/docs/extensibility/ux-guidelines/media/0903-05_infobar.png "0903&05;_InfoBar")  
  
 **Barra de informações com barra de progresso e a descrição textual**  
  
 ![Barra de informações dentro de uma janela](~/docs/extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903&06;_InfoBarInWindow")  
  
 **Barra de informações dentro da janela de análise de código**  
  
##### <a name="inline"></a>Embutido  
 Indicação de progresso embutido pode ser representada por qualquer um dos tipos de carregador de progresso. Normalmente o indicador de progresso é emparelhado com mensagens, mas isso não é um requisito.  
  
 ![Controle giratório de progresso embutido](~/docs/extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903&07;_InlineSpinner")  
  
 **Combinado com descrição textual de controle giratório**  
  
 ![Embutido empilhadas barras de progresso](~/docs/extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903&08;_InlineStackedProgress")  
  
 **Barras de progresso empilhadas determinada**  
  
 ![Mensagens de progresso embutido](~/docs/extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903&09;_InlineText")  
  
 **Texto do Server Explorer embutido: atualizando...**  
  
##### <a name="tool-windows"></a>Janelas de ferramenta  
 Indicação de progresso global é representada por uma barra de progresso indeterminado posicionada diretamente abaixo da barra de ferramentas.  
  
 ![Barra de progresso indeterminado global](~/docs/extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903&23;_GlobalIndeterminate")  
  
 **Barra de progresso indeterminado global do Team Explorer**  
  
##### <a name="dialogs"></a>Diálogos  
 Caixas de diálogo podem conter qualquer um dos tipos de carregador de progresso. Indicadores de progresso podem ser emparelhados com mensagens como combinados com vários níveis de indicação de progresso para representar granular e processos sub.  
  
 ![Caixa de diálogo com vários tipos de indicador de progresso](~/docs/extensibility/ux-guidelines/media/0903-11_dialog.png "0903&11;_Dialog")  
  
 **Caixa de diálogo Visual Studio com processos simultâneos e vários tipos de indicador de andamento**  
  
 ![Caixa de diálogo com o carregador de progresso e mensagens](~/docs/extensibility/ux-guidelines/media/0903-12_dialog2.png "0903&12;_Dialog2")  
  
 **Caixa de diálogo Visual Studio com o carregador de progresso e mensagens em linha de comando**  
  
##### <a name="document-well"></a>Documento bem  
 O documento também pode exibir vários tipos de carregador de progresso em combinação com controles.  
  
 ![Progresso de mensagens no documento bem](~/docs/extensibility/ux-guidelines/media/0903-13_documentwell.png "0903&13;_DocumentWell")  
  
 **Barra de progresso indeterminado abaixo da barra de ferramentas**  
  
##### <a name="output-window"></a>Janela Saída  
 A janela de saída é apropriada para manipular a progressão de processo e o status do andamento contínuo por meio de mensagens de texto embutido. Você deve usar a barra de Status junto com qualquer relatório de andamento de janela Saída.  
  
 ![Na janela de saída de mensagens de progresso](~/docs/extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903&14;_OutputWindow")  
  
 **Janela de saída com o status do processo contínuo e aguarde de mensagens**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a>Infobars  
  
### <a name="overview"></a>Visão Geral  
 Infobars dar ao usuário um indicador perto de seu ponto de atenção e usando o controle de barra de informações compartilhadas garante a consistência na aparência e interação.  
  
 ![Barra de informações](~/docs/extensibility/ux-guidelines/media/0904-01_infobar.png "0904&01;_Infobar")  
  
 **Infobars no Visual Studio**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>Uso apropriado para uma barra de informações  
  
-   Para dar ao usuário uma mensagem sem bloqueio, mas importante relevante ao contexto atual  
  
-   Para indicar que a interface do usuário está em um determinado estado ou condição que tem algumas implicações de interação, como histórico de depuração  
  
-   Para notificar o usuário que o sistema detectou problemas, como quando uma extensão está causando problemas de desempenho  
  
-   Para fornecer ao usuário uma maneira para facilmente adotar medidas, como quando o editor detecta que um arquivo tiver mistos tabulações e espaços  
  
##### <a name="do"></a>Faça:  
  
-   Mantenha o texto da mensagem de barra de informações curtas e para o ponto.  
  
-   Manter o texto nos links e botões sucinta.  
  
-   Certifique-se de fornecer aos usuários as opções de "ação" são mínimas, mostrando somente as ações necessárias.  
  
##### <a name="dont"></a>Não:  
  
-   Use uma barra de informações para oferecer comandos padrão que devem ser colocados em uma barra de ferramentas.  
  
-   Use uma barra de informações no lugar de uma caixa de diálogo modal.  
  
-   Crie uma mensagem flutuante fora de uma janela.  
  
-   Use vários infobars em vários locais dentro da mesma janela.  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Vários infobars pode mostrar ao mesmo tempo?  
 Sim, vários infobars pode mostrar ao mesmo tempo. Eles serão exibidos em ordem first-come, first-served com a barra de informações primeiro mostrando em mostrando infobars superior e adicionais abaixo.  
  
 O usuário verá um máximo de três infobars de uma vez, depois que, se infobars mais estiverem disponíveis, a região de barra de informações ficará rolável.  
  
### <a name="creating-an-infobar"></a>Criando uma barra de informações  
 Na barra de informações tem quatro seções, da esquerda para a direita:  
  
-   **Ícone:** isso é onde você adicionaria qualquer ícone você deseja exibir para a barra de informações, como um ícone de aviso.  
  
-   **Texto:** você pode adicionar texto para descrever o usuário cenário/situação é, junto com os links dentro do texto, se necessário. Lembre-se de manter o texto sucinta.  
  
-   **Ações:** nesta seção deve conter botões para ações que o usuário pode executar em sua barra de informações e links.  
  
-   **Botão Fechar:** a última seção à direita pode ter um botão Fechar.  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>Criar uma barra de informações padrão no código gerenciado  
 A classe InfoBarModel pode ser usada para criar uma fonte de dados para uma barra de informações. Use um desses quatro construtores:  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 Aqui está um exemplo que cria um InfoBarModel com algum texto com um hiperlink, um botão de ação e um ícone.  
  
 ![Barra de informações com hiperlink](~/docs/extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904&02;_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>Criando uma barra de informações padrão no código nativo  
 Implementar a interface de IVsInfoBar a fim de fornecer uma barra de informações do código nativo.  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Obtendo uma UIElement da barra de informações de uma barra de informações  
 A implementação InfoBarModel ou IVsInfoBar são modelos de dados que devem ser transformados em um UIElement para ser mostrado na interface do usuário. Um UIElement pode ser recuperado com o serviço de SVsInfoBarUIFactory/IVsInfoBarUIFactory.  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>Posicionamento  
 Infobars podem ser mostrados em um ou mais dos seguintes locais:  
  
-   Janelas de ferramenta  
  
-   Dentro de uma guia de documento  
  
> [!IMPORTANT]
>  É possível posicionar uma barra de informações para fornecer uma mensagem sobre o contexto global. Isso será exibido entre as barras de ferramentas e o documento bem. Isso não é recomendado porque ele causa problemas com "ir e puxão" do IDE e deve ser evitada, a menos que absolutamente necessárias e adequadas.  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>Colocar uma barra de informações em um ToolWindowPane  
 O método ToolWindowPane.AddInfoBar(IVsInfoBar) pode ser usado para adicionar uma barra de informações para uma janela de ferramenta. Esta API pode adicionar um IVsInfoBar (do qual InfoBarModel é uma implementação padrão), ou um IVsUIElement.  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Colocar uma barra de informações em um documento ou não ToolWindowPane  
 Para colocar uma barra de informações em qualquer IVsWindowFrame, use a propriedade VSFPROPID_InfoBarHost para obter o IVsInfoBarHost para o quadro e adicione a barra de informações UIElement.  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>Colocar uma barra de informações na janela principal  
 Para colocar uma barra de informações na janela principal, use VSSPROPID_MainWindowInfoBarHost do serviço IVsShell para obter IVsInfoBarHost da janela principal e adicione a barra de informações UIElement a ele.  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Saber quando o usuário executa a ação na minha barra de informações?  
 Sim, voltaremos cada ação de evento para o autor da barra de informações. Então, cabe ao autor da barra de informações agir no IDE com base na seleção do usuário na barra de informações. Infobars será removido automaticamente do host cujo fechar botão foi clicado, mas o trabalho adicional é necessário se outros infobars precisam ser removidos depois de fechar. Telemetria também precisará ser registrados independentemente por cada barra de informações.  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Recebendo eventos da barra de informações em um ToolWindowPane  
 ToolWindowPane tem dois eventos para infobars. O evento InfoBarClosed é gerado quando uma barra de informações no ToolWindowPane está fechada. O evento InfoBarActionItemClicked é gerado quando um hiperlink ou botão de barra de informações é clicado.  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Receber eventos de barra de informações diretamente no UIElement  
 IVsInfoBarUIElement.Advise pode ser usado para assinar eventos diretamente de UIElement de uma barra de informações. Implementar IVsInfoBarUIEvents permitirá que o autor de receber fechar e clique em eventos.  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a>Validação de erro  
 Quando um usuário insere informações que não é aceitáveis, como quando um campo obrigatório é ignorado ou quando os dados são inseridos no formato incorreto, é melhor usar controle validação ou comentários próximo ao controle em vez de usar uma caixa de diálogo de erro pop-up bloqueio.  
  
### <a name="field-validation"></a>Validação de campo  
 Validação de formulário e campo consiste em três componentes: um controle, um ícone e uma dica de ferramenta. Embora vários tipos de controles podem usar isso, uma caixa de texto será usada como exemplo.  
  
 ![Campo de validação (em branco)](~/docs/extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905&01;_FieldValidation")  
  
 Se o campo é obrigatório, deve haver marca d'água de texto informando ** \<necessária >** e o plano de fundo do campo deve ser clara amarelo (VSColor: `Environment.ControlEditRequiredBackground`) e o primeiro plano deve ser cinza (VSColor: `Environment.ControlEditRequiredHintText`):  
  
 ![Campo de validação com o rótulo "Required"](~/docs/extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905&02;_FieldValidationRequired")  
  
 O programa pode determinar que o controle está em um estado de *conteúdo inválido inserido* quando o foco é movido para um outro controle ou quando o usuário clica em um botão de confirmação [Okey] ou quando o usuário salva o documento ou formulário.  
  
 Quando o estado de conteúdo inválido é determinado, um ícone aparece dentro do controle ou ao lado dela. Uma dica de ferramenta que descreve o erro deve aparecer no foco do ícone ou do controle. Além disso, uma borda de 1 pixel deve aparecer em torno do controle que está criando o estado inválido.  
  
 ![Especificações de layout de validação de campo](~/docs/extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905&03;_LayoutSpecs")  
  
 **Especificações de layout para validação de campo**  
  
#### <a name="acceptable-variations-for-icon-location"></a>Variações aceitáveis para o local do ícone  
 Há inúmeros casos únicos em que os usuários precisam ser informado sobre erros de validação. Considerando o tipo de controle e a configuração da interface do usuário, escolha o posicionamento do ícone apropriado para sua situação.  
  
 ![Locais aceitáveis para o local do ícone](~/docs/extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905&04;_IconLocation")  
  
 **Variações aceitáveis para locais de ícone de validação de campo**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Exigir uma viagem para uma conexão de rede ou servidor de validação  
 Em alguns casos, um processamento para o servidor é necessária para verificar o conteúdo e seria importante mostrar o progresso do usuário, verificado e os estados de erro. A figura abaixo mostra um exemplo de caso e a interface do usuário recomendado.  
  
 ![Validação envolvendo um processamento para um servidor](~/docs/extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905&05;_RoundTrip")  
  
 **Validação envolvendo uma ida e volta a um servidor**  
  
 Observe que o espaço disponível adequado à direita do controle deve ser fornecido para acomodar "Verificando …" e o texto "Repetir".  
  
#### <a name="in-place-warning-text"></a>Texto de aviso no local  
 Quando houver espaço disponível para colocar a mensagem de erro perto do controle em um estado de erro, isso é preferível a usar a dica de ferramenta sozinha.  
  
 ![Aviso in-loco](~/docs/extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905&06;_InPlaceWarning")  
  
 **Texto de aviso no local**  
  
#### <a name="watermarks"></a>Marcas d'água  
 Às vezes, uma janela ou todo o controle está em um estado de erro. Nessa situação, use uma marca d'água para indicar o erro.  
  
 ![Marca d'água](~/docs/extensibility/ux-guidelines/media/0905-07_watermark.png "0905&07;_Watermark")  
  
 **Validação do campo de marca d'água**
