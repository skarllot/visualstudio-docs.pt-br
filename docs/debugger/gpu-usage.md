---
title: "Uso de GPU | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Uso de GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use a ferramenta de uso de GPU no Hub de diagnóstico de desempenho do Visual Studio e para melhor entender a utilização de hardware de alto nível do aplicativo Direct3D.  Você pode usá\-lo para determinar se o desempenho do seu aplicativo está vinculado à CPU ou associadas a GPU e obtenha informações sobre como você pode usar o hardware da plataforma com mais eficiência.  Uso de GPU oferece suporte a aplicativos que usam o Direct3D 12, Direct3D 11 e Direct3D 10; ele não oferece suporte a outros gráficos APIs como Direct2D ou OpenGL.  
  
 Este é o **relatório de uso de GPU** janela:  
  
 ![The GPU Usage report, with CPU and GPU timelines](../debugger/media/gfx_diag_gpu_usage_report.png "gfx\_diag\_gpu\_usage\_report")  
  
## Requisitos  
 A seguir estão os requisitos para usar a ferramenta uso de GPU que estão além dos requisitos de diagnóstico de gráficos.  
  
-   Uma GPU e drivers que oferecem suporte a instrumentação do tempo necessário.  
  
    > [!NOTE]
    >  Para obter mais informações sobre o hardware com suporte e drivers, consulte [Suporte de hardware e driver](#hwsupport) no final deste documento.  
  
 Para obter mais informações sobre os requisitos de diagnóstico de gráficos, consulte [Guia de Introdução](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## Usando a ferramenta de uso de GPU  
 Quando você executa seu aplicativo sob a ferramenta uso da GPU, o Visual Studio cria uma sessão de diagnóstico que gráficos informações gerais sobre o desempenho de renderização e a utilização da CPU em tempo real do seu aplicativo.  
  
#### Para iniciar a ferramenta uso da GPU:  
  
1.  No menu principal, escolha **Depurar**, em seguida, **desempenho e diagnóstico** \(teclado: pressione Alt \+ F2\).  
  
2.  No hub de desempenho e diagnóstico, marque a caixa ao lado **uso de GPU**.  Opcionalmente, marque as caixas ao lado de outras ferramentas que você está interessado.  Você pode executar o desempenho e diagnóstico várias ferramentas simultaneamente para obter uma imagem mais completa do desempenho do seu aplicativo.  
  
     ![Choose the diagnostic tools you want to use.](../debugger/media/gfx_diag_diagsession_tools.png "gfx\_diag\_diagsession\_tools")  
  
    > [!NOTE]
    >  Nem todas as ferramentas de desempenho e diagnóstico podem ser usadas ao mesmo tempo.  
  
3.  Escolha o azul **Iniciar** botão na parte inferior do hub desempenho e diagnóstico para executar seu aplicativo em ferramentas que você selecionou.  
  
 As informações de alto nível que são exibidas em tempo real incluem o prazo de quadro, taxa de quadros e a utilização da CPU.  Cada uma dessas partes de informações são mostrados independentemente, mas usar uma escala de tempo comum, para que você pode relacionar facilmente entre elas.  
  
 O **tempo \(ms\) do quadro** e **quadros por segundo \(FPS\)** gráficos contêm dois vermelho, horizontal linhas metas de desempenho que representam de 30 e 60 quadros por segundo.  No **tempo de quadro** gráfico, seu aplicativo está excedendo o destino de desempenho quando o gráfico está abaixo da linha e ausente\-lo quando o gráfico está acima da linha.  Para os quadros por segundo gráfico é o oposto – seu aplicativo está excedendo o destino de desempenho quando o gráfico está acima da linha e ausente\-lo quando o gráfico está abaixo da linha.  Basicamente, esses gráficos são usados para ter uma idéia de alto nível de desempenho do aplicativo e identificar atrasos que você talvez queira investigar – por exemplo, uma queda repentina na taxa de quadros ou um aumento na utilização da CPU.  
  
 Enquanto o aplicativo é executado sob a ferramenta uso da GPU, a sessão de diagnóstico também coleta informações detalhadas sobre eventos de gráficos que foram executados na GPU.  Essa informação é usada para gerar um relatório mais detalhado de como o seu aplicativo utiliza o hardware.  Como esse relatório leva algum tempo para gerar a partir das informações coletadas, só está disponível depois que a sessão de diagnóstico é feita a coleta de informações.  
  
 Quando você deseja observar um desempenho ou utilização execute mais de perto, parar de coletar informações de desempenho para que o relatório possa ser gerado.  
  
#### Para gerar e exibir o relatório de utilização de GPU:  
  
1.  Na parte inferior da janela da sessão de diagnóstico, escolha o **Parar de coletar** vincular ou pressione **Parar** no canto superior esquerdo.  
  
     ![Collect GPU and CPU timing information.](../debugger/media/gfx_diag_gpu_usage_collect.png "gfx\_diag\_gpu\_usage\_collect")  
  
2.  Na parte superior do relatório, selecione uma seção de um dos gráficos que mostra o problema que você deseja investigar.  A seleção pode ser até 3 segundos de tempo; mais seções são truncadas em direção ao início.  
  
     ![Post&#45;collection, select a range to view details](../debugger/media/gfx_diag_gpu_usage_select1.png "gfx\_diag\_gpu\_usage\_select1")  
  
3.  Na parte inferior do relatório, escolha o **Exibir detalhes** link no **... Clique aqui para exibir detalhes de uso da GPU para esse intervalo** mensagem para exibir um cronograma detalhado da sua seleção.  
  
     ![Post&#45;collection, with range selected](../debugger/media/gfx_diag_gpu_usage_select2.png "gfx\_diag\_gpu\_usage\_select2")  
  
 Isso abre um novo documento com guias que contém o relatório.  O relatório de uso de GPU ajuda você a ver quando um evento de gráficos é iniciado na CPU, quando ele atinge a GPU e quanto tempo leva a GPU para executá\-lo.  Essas informações podem ajudá\-lo a identificar afunilamentos e oportunidades de paralelismo maior em seu código.  
  
## Usando o relatório de uso de GPU  
 A parte superior do relatório de uso de GPU exibe linhas do tempo de atividade, atividade de renderização da GPU e atividade de cópia GPU de processamento da CPU.  Esses cronogramas são separadas por barras verticais, luz cinza que representam vsync da tela; a frequência das barras corresponde a taxa de atualização de um a exibe \(selecionado usando o **exibição** suspensa\) esses dados de uso de GPU foram coletados do.  Porque a exibição pode ter uma taxa de atualização mais alta que o destino de desempenho do seu aplicativo pode não haver uma relação de 1 para 1 entre vsync e taxa de quadros que você deseja que seu aplicativo para obter.  Para atender a sua meta de desempenho um aplicativo deve concluir todo o processamento, executar processamento e fazer uma chamada de Present\(\) em que a taxa de quadros de destino, mas o quadro processado não será exibido até que o próximo vsync após Present\(\).  
  
 A parte inferior exibe uma lista dos eventos de gráficos que ocorreram durante o período do relatório.  
  
 Aqui está o **relatório de uso de GPU** janela:  
  
 ![The GPU Usage report, with CPU and GPU timelines](../debugger/media/gfx_diag_gpu_usage_report.png "gfx\_diag\_gpu\_usage\_report")  
  
 Selecionar um dos eventos na parte inferior do relatório coloca um marcador em eventos correspondentes nas linhas do tempo relevantes, normalmente um evento em um thread de CPU que representa a chamada de API e outro evento em um os cronogramas de GPU que representa quando a GPU concluído a tarefa.  Da mesma forma, selecionar um dos eventos em uma linha do tempo destaca o evento correspondente na parte inferior do relatório. Quando ampliado de linhas de tempo na parte superior do relatório, somente os eventos mais demorados são visíveis.  Para ver os eventos que têm uma duração menor, ampliar os cronogramas usando Ctrl \+ roda em seu dispositivo apontador, ou o controle de dimensionamento no canto inferior esquerdo do painel superior.  Você também pode arrastar o conteúdo do painel de linha do tempo para percorrer os eventos registrados.  
  
 Para ajudá\-lo a encontrar o que procura, você pode filtrar o relatório de uso de GPU com base em nomes de processo, Thread IDs e o nome do evento; Além disso, você pode escolher a taxa de atualização do vídeo que determina as linhas vysnc e você pode classificar eventos hierarquicamente, se seu aplicativo usa a interface ID3DUserDefinedAnnotation para comandos de processamento do grupo.  
  
 Aqui estão mais detalhes:  
  
|Controle de filtro|Descrição|  
|------------------------|---------------|  
|**Processo**|O nome do processo que lhe interessam.  Todos os processos que usado GPU durante a sessão de diagnóstico estão incluídos nesse menu suspenso.  A cor associada com o processo essa lista suspensa é a cor da atividade do thread nas linhas do tempo abaixo.|  
|**Thread**|A ID do thread que lhe interessam.  Em um aplicativo multithread, isso pode ajudar a isolar threads específicos que pertencem ao processo que você está interessado.  Eventos associados com o thread selecionado são realçados em cada linha do tempo.|  
|**Exibir**|O número da exibição cuja taxa de atualização é exibida **Note:**  Alguns drivers podem ser configurados para apresentar vários monitores físicos como uma exibição virtual única, grande.  Você poderá ver apenas uma exibição, listada, mesmo se o computador tiver vários monitores conectados.|  
|**Filtrar**|Palavras\-chave que você está interessado.  Eventos na parte inferior do relatório incluirão apenas aqueles que correspondem a uma palavra\-chave no todo ou em parte.  Você pode especificar várias palavras\-chave, separando\-os com um ponto e vírgula \(;\).|  
|**Classificação de hierarquia**|Uma caixa de seleção que indica se a hierarquias de evento – definidas por meio de marcadores do usuário – são preservadas ou ignoradas.|  
  
 A lista de eventos na parte inferior do relatório de utilização de GPU exibe os detalhes de cada evento.  
  
|Coluna|Descrição|  
|------------|---------------|  
|**Nome do Evento**|O nome do evento de gráficos.  Um evento normalmente corresponde a um evento na linha de tempo da CPU do thread e um evento em um cronograma GPU.<br /><br /> Nomes de eventos podem ser 'unattributed' se o uso de GPU não pôde determinar o nome de um evento.  Para obter mais informações, consulte a observação abaixo desta tabela.|  
|**Início da CPU \(ns\)**|A hora em que o evento foi iniciado na CPU, chamando uma API do Direct3D.  O tempo é medido em nanossegundos, relativo ao quando o aplicativo é iniciado.|  
|**Início da GPU \(ns\)**|A hora em que o evento foi iniciado na GPU.  O tempo é medido em nanossegundos, relativo ao quando o aplicativo é iniciado.|  
|**Duração da GPU \(ns\)**|A hora em que o evento levou para ser concluído na GPU, em nanossegundos.|  
|**Nome do Processo**|O nome do aplicativo do qual o evento se originou.|  
|**ID do Thread**|A ID do thread de onde veio o evento.|  
  
> [!IMPORTANT]
>  Windows 8.1 é necessária para atribuição de evento.  Além disso, se sua GPU ou driver não oferecem suporte os recursos de instrumentação necessária, todos os eventos aparecerá como 'unattributed'.  Certifique\-se de atualizar o driver da GPU e tente novamente caso ocorra esse problema.  Para obter mais informações, consulte [Suporte de hardware e driver](#hwsupport) abaixo.  
  
## Configurações de uso de GPU  
 Você pode configurar a ferramenta de uso da GPU para adiar a coleção de informações de criação de perfil, em vez de começar a coletar informações como o aplicativo é iniciado.  Como o tamanho das informações de criação de perfil pode ser significativo, isso é útil quando você sabe que a lentidão no desempenho do aplicativo não será exibido até mais tarde.  
  
#### Adiar a criação de perfil desde o início do aplicativo:  
  
1.  No menu principal, escolha **Depurar**, em seguida, **desempenho e diagnóstico** \(teclado: pressione Alt \+ F2\).  
  
2.  No hub de desempenho e diagnóstico, execute o **configurações** próximo ao link **uso de GPU**.  
  
3.  Em **configuração de criação de perfil de GPU**, no **geral** página de propriedade, desmarque o **criação de perfil na inicialização do aplicativo** caixa de seleção para adiar a criação de perfil.  
  
     ![Configure when GPU Usage collection starts](../debugger/media/gfx_diag_gpu_usage_config.png "gfx\_diag\_gpu\_usage\_config")  
  
> [!IMPORTANT]
>  Adiar a criação de perfil não é suportada para aplicativos Direct3D 12.  
  
 Quando você adiar a coleção de informações de perfil usando essa configuração, um link adicional se torna disponível na parte inferior da janela de ferramenta do uso de GPU quando você executa seu aplicativo sob a ferramenta uso da GPU.  Para começar a coletar informações de perfil, escolha o **Iniciar** vincular o **Iniciar coleta adicionais detalhadas dados de uso de GPU** mensagem.  
  
##  <a name="hwsupport"></a> Suporte de hardware e driver  
 O seguinte hardware GPU e os drivers são suportados:  
  
|Fornecedor|Descrição de GPU|Versão de driver necessária|  
|----------------|----------------------|---------------------------------|  
|Intel ®|4ª geração processadores Intel ® Core \('Haswell'\)<br /><br /> -   Intel ® HD Graphics \(GT1\)<br />-   Intel ® HD Graphics 4200 \(GT2\)<br />-   Intel ® HD Graphics 4400 \(GT2\)<br />-   Intel ® HD Graphics 4600 \(GT2\)<br />-   Gráficos de alta definição Intel ® P4600 \(GT2\)<br />-   Gráficos de alta definição Intel ® P4700 \(GT2\)<br />-   Gráficos de alta definição Intel ® 5000 \(GT3\)<br />-   Gráficos Intel ® íris ™ 5100 \(GT3\)<br />-   Intel ® íris ™ Pro gráficos 5200 \(GT3e\)|\-\- \(use os drivers mais recentes\)|  
|AMD ®|Maioria desde AMD Radeon ™ HD 7000 série \(exclui AMD Radeon ™ HD 7350 7670\)<br /><br /> Aceleradores AMD Radeon ™ GPU, AMD FirePro ™ GPUs e AMD FirePro GPU com arquitetura de elementos gráficos principais próxima \(GCN\).<br /><br /> Série E AMD ® e AMD série acelerado processamento unidades \(APUs\) com a arquitetura de elementos gráficos principais próxima \(GCN\) \('Kaveri', 'Kabini', 'Temash', 'Beema', 'Mullins'\)|14,7 RC3 ou superior|  
|NVIDIA ®|Mais desde NVIDIA ® GeForce ® série 400.<br /><br /> Aceleradores NVIDIA ® GeForce ® GPUs NVIDIA Quadro ® GPUs e NVIDIA ® Tesla ™ GPU com arquitetura Fermi ™, Kepler ™ ou Oliveira ™.|343.37 ou superior|  
  
 Não há suporte para configurações de várias GPUS como NVIDIA ® SLI ™ e AMD Crossfire ™ neste momento.  Há suporte para a configuração de elementos gráficos híbridos, como NVIDIA ® Optimus ™ e AMD Enduro ™.  
  
## Consulte também  
  
-   [Resolver os problemas difíceis de gráficos com o jogo usando DirectX ferramentas \(vídeo\)](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
  
-   [Ferramenta de uso de GPU no Visual Studio \(vídeo\)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
  
-   [Ferramenta de uso de GPU no Visual Studio 2013 atualização 4 CTP1 \(blog\)](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx)  
  
-   [Uso de GPU do DirectX no Visual Studio \(blog\)](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx)