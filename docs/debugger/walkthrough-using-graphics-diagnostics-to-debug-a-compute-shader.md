---
title: "Instru&#231;&#245;es passo a passo: usando diagn&#243;stico de gr&#225;fico para depurar um sombreador computado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: usando diagn&#243;stico de gr&#225;fico para depurar um sombreador computado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo demonstra como usar as ferramentas de diagnóstico de gráficos do Visual Studio para investigar um sombreador de computação que gera resultados incorretos.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Usando o **lista de eventos gráficos** para localizar possíveis fontes do problema.  
  
-   Usando o **pilha de chamadas do evento de gráficos** para determinar qual calcular o sombreador é executado por um DirectCompute `Dispatch` eventos.  
  
-   Usando o **estágios de Pipeline gráficos** janela e HLSL do depurador para examinar o sombreador de computação que é a origem do problema.  
  
## Cenário  
 Nesse cenário, você tenha escrito uma simulação dinâmica de fluidos que usa DirectCompute para executar as partes com uso intensivo de computação da atualização de simulação.  Quando o aplicativo é executado, o processamento de conjunto de dados e da interface do usuário a aparência correta, mas a simulação não se comportar conforme o esperado.  Usando o diagnóstico de gráficos, você pode capturar o problema em um log de gráficos para que você pode depurar o aplicativo.  O problema parece com isto no aplicativo:  
  
 ![The simulated fluid behaves incorrectly.](~/docs/debugger/graphics/media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx\_diag\_demo\_compute\_shader\_fluid\_problem")  
  
 Para obter informações sobre como detectar os problemas de gráficos em um log de gráficos, consulte [Capturando informações de gráficos](../debugger/capturing-graphics-information.md).  
  
## Investigação  
 Você pode usar as ferramentas de diagnóstico de gráficos para carregar o arquivo de log de gráficos, de modo que você pode inspecionar os quadros capturados.  
  
#### Para examinar um quadro em um log de gráficos  
  
1.  No Visual Studio, carregue um log de gráficos que contém um quadro que exibe os resultados de simulação incorreto.  Uma nova guia de diagnóstico de gráficos aparece no Visual Studio.  Na parte superior dessa guia é a saída de destino de renderização do quadro selecionado.  Na parte inferior é parte do **lista de quadros**, que exibe uma miniatura de cada quadro capturado.  
  
2.  No **lista de quadros**, selecione um quadro que demonstra o comportamento incorreto de simulação.  Mesmo que o erro é exibido no código a simulação e não o código de processamento, você ainda precisa escolher um quadro porque DirectCompute eventos são capturados em uma base por quadro, junto com eventos do Direct3D.  Nesse cenário, os gráficos de log guia é semelhante ao seguinte:  
  
     ![The graphics log document in Visual Studio.](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode usar o **lista de eventos gráficos** para diagnosticar a ele.  O **lista de eventos gráficos** contém um evento para cada chamada DirectCompute e uma chamada de API da Direct3D que foi feita durante o quadro ativo — por exemplo, chamadas de API para executar uma computação na GPU, ou para processar o conjunto de dados ou a interface do usuário.  Nesse caso, estamos interessados em `Dispatch` eventos que representam partes da simulação executados na GPU.  
  
#### Para encontrar o evento de envio para a atualização de simulação  
  
1.  Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **lista de eventos** para abrir o **lista de eventos de gráficos** janela.  
  
2.  Inspecione o **lista de eventos gráficos** para o evento de desenho que renderiza o conjunto de dados.  Para tornar isso mais fácil, digite `Desenhar` no **pesquisa** caixa no canto superior direito do **lista de eventos gráficos** janela.  Isso filtra a lista para que ele contém apenas os eventos que têm "Desenha" em seus cargos.  Nesse cenário, você descobre que elas desenhar eventos ocorreu:  
  
     ![The Event List &#40;EL&#41; shows draw events.](~/docs/debugger/graphics/media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_2")  
  
3.  Percorrer cada evento de desenho enquanto você observa o destino de renderização na guia de documento de log de gráficos.  
  
4.  Pare quando o destino de renderização exibe o conjunto de dados processado pela primeira vez.  Nesse cenário, o conjunto de dados é processado no primeiro evento de desenho.  Erro na simulação é mostrado:  
  
     ![This draw event renders the simulation data set.](~/docs/debugger/graphics/media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_3")  
  
5.  Agora inspecionar o **lista de eventos gráficos** para o `Dispatch` eventos que atualiza a simulação.  Como é provável que a simulação está atualizada antes de ser processado, você pode se concentrar primeiro na `Dispatch` eventos que ocorrem antes do evento de desenho que renderiza os resultados.  Para tornar isso mais fácil, modifique o **pesquisa** caixa ler `Draw; expedição; CSSetShader (`.  Isso filtra a lista para que ele contém também `Dispatch` e `CSSetShader` eventos além de eventos de desenho.  Nesse cenário, você descobre que várias `Dispatch` eventos ocorridos antes do evento de desenho:  
  
     ![The EL shows draw, Dispatch and CSSetShader events](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_4")  
  
 Agora que você sabe que poucos potencialmente muitos `Dispatch` eventos pudesse corresponder ao problema, você pode examiná\-los mais detalhadamente.  
  
#### Para determinar qual calcular uma chamada de expedição de sombreador é executado  
  
1.  Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **pilha de chamadas do evento** para abrir o **pilha de chamadas do evento de gráficos** janela.  
  
2.  A partir do evento de desenho que renderiza os resultados de simulação, retroceder cada anterior `CSSetShader` eventos.  Em seguida, no **pilha de chamadas do evento de gráficos** janela, escolha a função principal para navegar até o site de chamada.  No site de chamada, você pode usar o primeiro parâmetro do [CSSetShader](http://msdn.microsoft.com/library/ff476402.aspx) chamada para determinar qual calcular o sombreador é executado da próxima de função `Dispatch` eventos.  
  
 Nesse cenário, há três pares de `CSSetShader` e `Dispatch` eventos em cada quadro.  Trabalhando com versões anteriores, o terceiro par representa a etapa de integração \(onde as partículas fluidas, na verdade, são movidas\), o segundo representa par o cálculo de força de etapa \(onde é calculada a força que afetam cada partícula\) e o primeiro par representa a etapa de cálculo de densidade.  
  
#### Para depurar o sombreador de computação  
  
1.  Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **estágios de Pipeline** para abrir o **estágios de Pipeline gráficos** janela.  
  
2.  Selecione a terceira `Dispatch` eventos \(aquela que precede o evento de desenho\) e, em seguida, no **estágios de Pipeline gráficos** janela, sob o **sombreador de computação** estágio, escolha **Iniciar depuração**.  
  
     ![Selecting the third Dispatch event in the EL.](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_6")  
  
     O depurador HLSL é iniciado ao sombreador que executa a etapa de integração.  
  
3.  Examine o código\-fonte do sombreador de cálculo para a etapa de integração procurar a origem do erro.  Quando você usar o diagnóstico de gráficos para depurar o código do sombreador de cálculo HLSL, você pode percorrer o código e usar outras ferramentas de depuração familiares, como janelas de observação.  Nesse cenário, você determinar que não parece haver um erro no sombreador de computação que executa a etapa de integração.  
  
     ![Debugging the IntegrateCS compute shader.](~/docs/debugger/graphics/media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_7")  
  
4.  Para parar a depuração do sombreador de computação, no **Depurar** barra de ferramentas, escolha **parar depuração** \(teclado: Shift \+ F5\).  
  
5.  Em seguida, selecione a segunda `Dispatch` evento e inicie a depuração do sombreador de computação, como você fez na etapa anterior.  
  
     ![Selecting the second Dispatch event in the EL.](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_8")  
  
     O depurador HLSL é iniciado no sombreador que calcula as forças que atuam em cada partícula fluida.  
  
6.  Examine o código fonte do sombreador computação para a etapa de força de cálculo.  Nesse cenário, você determinar que a origem do erro está aqui.  
  
     ![Debugging the ForceCS&#95;Simple compute shader.](~/docs/debugger/graphics/media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_9")  
  
 Depois de determinar o local do erro, você pode parar a depuração e modificar o código\-fonte do sombreador de cálculo para calcular a distância entre as partículas interagir corretamente.  Nesse cenário, basta alterar a linha `float2 diff = N_position + P_position;` para `float2 diff = N_position - P_position;`:  
  
 ![The corrected compute&#45;shader code.](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_10")  
  
 Nesse cenário, porque os sombreadores de computação são compilados em tempo de execução, você pode simplesmente reiniciar o aplicativo depois de fazer as alterações para observar como eles afetam a simulação.  Você não precisa recompilar o aplicativo.  Quando você executa o aplicativo, você descobre que a simulação agora funcione corretamente.  
  
 ![The simulated fluid behaves correctly.](../debugger/media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx\_diag\_demo\_compute\_shader\_fluid\_resolution")