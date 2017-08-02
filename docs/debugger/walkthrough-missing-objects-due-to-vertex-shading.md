---
title: "Instru&#231;&#245;es passo a passo: objetos ausentes devido ao sombreamento de v&#233;rtice | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: objetos ausentes devido ao sombreamento de v&#233;rtice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo demonstra como usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de diagnóstico de gráficos para investigar um objeto que está faltando devido a um erro que ocorre durante o estágio de sombreador de vértice.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Usando o **lista de eventos gráficos** para localizar possíveis fontes do problema.  
  
-   Usando o **estágios de Pipeline gráficos** janela para verificar o efeito do `DrawIndexed` chamadas de API do Direct3D.  
  
-   Usando o **depurador HLSL** para examinar o sombreador de vértices.  
  
-   Usando o **pilha de chamadas do evento de gráficos** para ajudar a localizar a origem de uma constante HLSL incorreta.  
  
## Cenário  
 Uma das causas comuns de um objeto ausente em um aplicativo 3D ocorre quando o sombreador de vértices transforma os vértices do objeto de modo incorreto ou inesperado — por exemplo, o objeto pode ser dimensionado para um tamanho muito pequeno ou transformado, de modo que ele seja exibido por trás da câmera, em vez de na frente dele.  
  
 Nesse cenário, quando o aplicativo é executado para testá\-lo, o plano de fundo é renderizado conforme o esperado, mas um dos objetos não aparecerá. Usando o diagnóstico de gráficos, você captura o problema para um log de gráficos para que você pode depurar o aplicativo. O problema parece com isso no aplicativo:  
  
 ![O objeto não pode ser visto.](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_problem.png "gfx\_diag\_demo\_missing\_object\_shader\_problem")  
  
## Investigação  
 Usando as ferramentas de diagnóstico de gráficos, você pode carregar o arquivo de log de gráficos para inspecionar os quadros que foram capturados durante o teste.  
  
#### Para examinar um quadro em um log de gráficos  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], carregar um log de gráficos que contém um quadro que exibe o objeto ausente. Uma nova guia do log de gráficos aparece no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Na parte superior desta guia é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe cada quadro capturado como uma imagem em miniatura.  
  
2.  No **lista quadro**, selecione um quadro que demonstra que o objeto não é exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, os gráficos de log guia é semelhante ao seguinte:  
  
     ![O documento de log de elementos gráficos no Visual Studio](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_1.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode começar a diagnosticá\-lo usando o **lista de eventos gráficos**. O **lista de eventos gráficos** contém todas as chamadas de API da Direct3D que foi feita para processar o quadro ativo, por exemplo, chamadas de API para configurar o estado do dispositivo, para criar e atualizar buffers e desenhar objetos que aparecem no quadro. Muitos tipos de chamadas são interessantes porque há normalmente \(mas nem sempre\) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado, por exemplo desenhar, expedição, copiar ou chamadas claras. Chamadas de desenho são particularmente interessantes porque cada um deles representa a geometria que o aplicativo processado \(chamadas de expedição também podem processar geometria\).  
  
 Porque você sabe que o objeto ausente não é que está sendo desenhado no alvo processado \(neste caso\) — mas que o restante da cena é desenhado conforme esperado — você pode usar o **lista de eventos gráficos** junto com o **estágios de Pipeline gráficos** tool para determinar qual desenhar o chamada corresponde à geometria do objeto ausente. O **estágios de Pipeline gráficos** janela mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito sobre o destino de renderização. Percorrer as chamadas de desenho, os estágios de pipeline são atualizados para mostrar a geometria que está associada essa chamada, e a saída de destino de renderização é atualizada para mostrar o estado do destino de renderização depois que a chamada foi concluída.  
  
#### Para localizar a chamada de desenho de geometria ausente  
  
1.  Abra o **lista de eventos gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **lista de eventos**.  
  
2.  Abra o **estágios de Pipeline gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **estágios de Pipeline**.  
  
3.  Percorrer cada chamada de desenho **lista de eventos gráficos** janela, assista a **estágios de Pipeline gráficos** janela para o objeto ausente. Para facilitar essa tarefa, digite "Desenhar" no **pesquisa** caixa no canto superior direito do **lista de eventos gráficos** janela. Isso filtra a lista para que ele contém apenas os eventos que têm "Desenhar" em seus cargos.  
  
     No **estágios de Pipeline gráficos** janela, o **entrada do Assembler** estágio mostra a geometria do objeto antes de transformados e o **sombreador de vértices** estágio mostra o mesmo objeto depois que ele é transformado. Nesse cenário, você sabe que você encontrou do objeto quando ele for exibido no **entrada do Assembler** estágio e nada é exibido no **sombreador de vértices** estágio.  
  
    > [!NOTE]
    >  Se outros estágios de geometria — por exemplo, os estágios de sombreador Hull, sombreador de domínio ou Geometry Shader — processar o objeto, eles podem ser a causa do problema. Normalmente, o problema está relacionado ao estágio de mais recente em que o resultado não é exibido ou é exibido de forma inesperada.  
  
4.  Pare quando atingir a chamada de desenho que corresponde ao objeto ausente. Nesse cenário, o **estágios de Pipeline gráficos** janela indica que a geometria foi emitida para a GPU \(indicada pela miniatura Assembler de entrada\), mas não aparecem no alvo de renderização porque algo deu errado durante o estágio de sombreador de vértices \(indicado pela miniatura sombreador de vértices\):  
  
     ![Um evento de DrawIndexed e seu efeito sobre o pipeline](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_2.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_2")  
  
 Depois de confirmar que o aplicativo emitiu uma chamada de desenho de geometria do objeto ausente e descobrir que o problema ocorre durante o estágio de sombreador de vértices, você pode usar o depurador HLSL para examinar o sombreador de vértices e descubra o que aconteceu com a geometria do objeto. Você pode usar o depurador HLSL para examinar o estado de HLSL variáveis durante a execução, percorrer o código HLSL e defina pontos de interrupção para ajudá\-lo a diagnosticar o problema.  
  
#### Para examinar o sombreador de vértices  
  
1.  Inicie a depuração do estágio do sombreador de vértice. No **estágios de Pipeline gráficos** janela, no **sombreador de vértices** estágio, escolha o **Iniciar depuração** botão.  
  
2.  Porque o **entrada do Assembler** estágio aparece para fornecer dados para o sombreador de vértices e **sombreador de vértices** estágio parece não produzem nenhuma saída, convém examinar a estrutura de saída do sombreador de vértice, `output`. Como percorrer o código HLSL, você levar perto examinar quando `output` é modificado.  
  
3.  Na primeira vez que `output` é modificado, o membro `worldPos` é gravado.  
  
     ![O valor de "output.worldPos" aparece razoável](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_4.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_4")  
  
     Como seu valor parece ser razoável, você continuar percorrendo o código até a próxima linha modifica `output`.  
  
4.  Na próxima vez que `output` é modificado, o membro `pos` é gravado.  
  
     ![O valor de "output.pos" foi zerado](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_5.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_5")  
  
     Neste momento, o valor da `pos` membro — todos os zeros — parecer suspeito. Em seguida, você deseja determinar como `output.pos` passou a ter um valor de zeros.  
  
5.  Observe que `output.pos` leva seu valor de uma variável chamada `temp`. Na linha anterior, você vê que o valor de `temp` é o resultado da multiplicação do valor anterior por uma constante chamada `projection`. Você suspeita que `temp`do valor suspeita é o resultado dessa multiplicação. Quando você posiciona o ponteiro no `projection`, você notar que o seu valor é também todos os zeros.  
  
     ![A matriz de projeção contém uma transformação incorreta](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_6.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_6")  
  
     Nesse cenário, a análise revela que `temp`do valor suspeito provavelmente é causado pelo seu multiplicação por `projection`, e porque `projection` é uma constante que é indicado para conter uma matriz de projeção, você sabe que ele não deve conter todos os zeros.  
  
 Depois de determinar que a constante HLSL `projection`— passado para o sombreador pelo seu aplicativo — é a origem provável do problema, a próxima etapa é encontrar o local no código\-fonte do aplicativo em que o buffer de constante é preenchido. Você pode usar o **pilha de chamadas do evento de gráficos** para encontrar esse local.  
  
#### Para localizar onde a constante é definida no código\-fonte do aplicativo  
  
1.  Abra o **pilha de chamadas do evento de gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **pilha de chamadas do evento de gráficos**.  
  
2.  Navegue até a pilha de chamada no código\-fonte do aplicativo. No **pilha de chamadas do evento de gráficos** janela, escolha a chamada principal para ver se o buffer constante lá está sendo preenchido. Se não estiver, continue a pilha de chamadas até encontrar onde ele está sendo preenchido. Nesse cenário, você descobre que o buffer constante está sendo preenchido — usando o `UpdateSubresource` API do Direct3D — ainda mais para cima a pilha de chamadas em uma função chamada `MarbleMaze::Render`, e seu valor proveniente de um objeto de buffer constante chamada `m_marbleConstantBufferData`:  
  
     ![O código que define o buffer de constante do objeto](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_7.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_7")  
  
    > [!TIP]
    >  Se você estiver depurando simultaneamente seu aplicativo, você pode definir um ponto de interrupção nesse local e será atingido quando o próximo quadro é renderizado. Em seguida, você pode inspecionar os membros de `m_marbleConstantBufferData` para confirmar se o valor da `projection` membro é definido como zeros quando o buffer de constante é preenchido.  
  
 Depois de encontrar o local onde o buffer constante está sendo preenchido e descobrir que seus valores provenientes da variável `m_marbleConstantBufferData`, a próxima etapa é descobrir onde o `m_marbleConstantBufferData.projection` é definido como zeros. Você pode usar **Localizar todas as referências** examinar rapidamente para o código que altera o valor de `m_marbleConstantBufferData.projection`.  
  
#### Para localizar onde o membro de projeção é definido no código\-fonte do aplicativo  
  
1.  Localizar referências a `m_marbleConstantBufferData.projection`. Abra o menu de atalho para a variável `m_marbleConstantBufferData`, e, em seguida, escolha **Localizar todas as referências**.  
  
2.  Para navegar até o local da linha no código\-fonte do aplicativo onde o `projection` membro é modificado, escolha a linha no **Find Symbol Results** janela. Porque o primeiro resultado que modifica o membro de projeção não pode ser a causa do problema, você talvez precise examinar várias áreas do código\-fonte do aplicativo.  
  
 Depois de localizar o local onde `m_marbleConstantBufferData.projection` estiver definido, você pode examinar o código\-fonte ao redor para determinar a origem do valor incorreto. Nesse cenário, você descobre que o valor de `m_marbleConstantBufferData.projection` é definido como uma variável local denominada `projection` antes que ela foi inicializada com um valor que é fornecido pelo código `m_camera->GetProjection(&projection);` na próxima linha.  
  
 ![A projeção de mármore é definida antes da inicialização](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_9.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_9")  
  
 Para corrigir o problema, você move a linha de código que define o valor de `m_marbleConstantBufferData.projection` após a linha que inicializa o valor da variável local `projection`.  
  
 ![O código&#45;fonte C&#43;&#43; corrigido](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_step_10.png "gfx\_diag\_demo\_missing\_object\_shader\_step\_10")  
  
 Depois de corrigir o código, você pode recriá\-lo e executar o aplicativo novamente para descobrir o que é resolvido o problema de renderização:  
  
 ![O objeto agora é exibido.](~/debugger/graphics/media/gfx_diag_demo_missing_object_shader_resolution.png "gfx\_diag\_demo\_missing\_object\_shader\_resolution")