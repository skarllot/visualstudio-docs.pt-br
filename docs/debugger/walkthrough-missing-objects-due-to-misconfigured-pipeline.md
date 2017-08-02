---
title: "Instru&#231;&#245;es passo a passo: objetos ausentes devido ao pipeline configurado incorretamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: objetos ausentes devido ao pipeline configurado incorretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo demonstra como usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de diagnóstico de gráficos para investigar um objeto que está faltando devido a um sombreador de pixel não definida.  
  
 Este passo a passo ilustra essas tarefas:  
  
-   Usando o **lista de eventos gráficos** para localizar possíveis fontes do problema.  
  
-   Usando o **estágios de Pipeline gráficos** janela para examinar o efeito do `DrawIndexed` chamada à API do Direct3D.  
  
-   Inspecionando o contexto de dispositivo para confirmar que um estágio de sombreador não foi definido.  
  
-   Usando o **estágios de Pipeline gráficos** janela junto com o **pilha de chamadas do evento de gráficos** para ajudar a localizar a origem do sombreador de pixel não definida.  
  
## Cenário  
 Quando um objeto está ausente em um aplicativo 3D, às vezes, é porque um dos estágios de sombreador não está definido antes do objeto é processado. Em aplicativos que têm necessidades de processamento simples, a origem do erro é geralmente localizada em algum lugar na pilha de chamadas de chamada de desenho do objeto. No entanto, como uma otimização, alguns objetos de lote juntos de aplicativos com programas de sombreador, texturas ou outros dados em comum para minimizar a alteração de estadom sobrecarga. Em um desses aplicativos, a origem do erro pode ser enterrada no sistema de envio em lote, em vez de localizado na pilha de chamadas da chamada de desenho. O cenário neste passo a passo demonstra um aplicativo que precisa de processamento simples, e então a origem do erro pode ser encontrada na pilha de chamadas.  
  
 Nesse cenário, quando o aplicativo é executado para testá\-lo, o plano de fundo é renderizado conforme o esperado, mas um dos objetos não aparece. Usando o diagnóstico de gráficos, você captura o problema para um log de gráficos para que você pode depurar o aplicativo. O problema parece com isso no aplicativo:  
  
 ![O objeto não pode ser visto](~/debugger/graphics/media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx\_diag\_demo\_misconfigured\_pipeline\_problem")  
  
## Investigação  
 Usando as ferramentas de diagnóstico de gráficos, você pode carregar o documento de log de gráficos para inspecionar os quadros que foram capturados durante o teste.  
  
#### Para examinar um quadro em um log de gráficos  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], carregar um documento de log de gráficos que contém um quadro que exibe o objeto ausente. Uma nova guia do log de gráficos aparece no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Na parte superior desta guia é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe cada quadro capturado como uma imagem em miniatura.  
  
2.  No **lista quadro**, selecione um quadro que demonstra que o objeto não é exibido. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, os gráficos de log guia é semelhante ao seguinte:  
  
     ![O documento de log de elementos gráficos no Visual Studio](~/debugger/graphics/media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx\_diag\_demo\_misconfigured\_pipeline\_step\_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode começar a diagnosticá\-lo usando o **lista de eventos gráficos**. O **lista de eventos gráficos** contém todas as chamadas de API da Direct3D que foi feita para processar o quadro ativo — por exemplo, para configurar o estado do dispositivo, para criar e atualizar buffers e desenhar objetos que aparecem no quadro. Muitos tipos de chamadas — por exemplo, desenho, expedição, copiar ou desmarque chamadas — são interessantes porque há normalmente \(mas nem sempre\) uma alteração correspondente no destino de renderização quando o aplicativo está funcionando conforme o esperado. Chamadas de desenho são particularmente interessantes porque cada um deles representa a geometria que o aplicativo processado.  
  
 Porque você sabe que o destino de renderização não contém o ausente objeto mas também que não parece haver outros erros, você pode usar o **lista de eventos gráficos** junto com o **estágios de Pipeline gráficos** tool para determinar qual desenhar o chamada corresponde à geometria do objeto ausente. O **estágios de Pipeline gráficos** janela mostra a geometria que foi enviada para cada chamada de desenho, independentemente de seu efeito sobre o destino de renderização. Como percorrer as chamadas de desenho, os estágios de pipeline são atualizados para mostrar a geometria associado com cada chamada conforme ela flui pelo cada estágio habilitado e a saída de destino de renderização é atualizada para mostrar o estado do destino de renderização depois que a chamada é concluída.  
  
#### Para localizar a chamada de desenho de geometria ausente  
  
1.  Abra o **lista de eventos gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **lista de eventos**.  
  
2.  Abra o **estágios de Pipeline gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **estágios de Pipeline**.  
  
3.  Percorrer cada chamada de desenho **lista de eventos gráficos** janela, assista a **estágios de Pipeline gráficos** janela para o objeto ausente. Para facilitar essa tarefa, digite "Desenhar" no **pesquisa** caixa no canto superior direito do **lista de eventos gráficos** janela. Isso filtra a lista para que ele contém apenas os eventos que têm "Desenhar" em seus cargos.  
  
     No **estágios de Pipeline gráficos** janela, o **entrada do Assembler** estágio mostra a geometria do objeto antes que ele é transformado e o **sombreador de vértices** estágio mostra o mesmo objeto depois que ele é transformado. Nesse cenário, observe que o **estágios de Pipeline gráficos** janela mostra o **entrada do Assembler** e  **sombreador de vértices** estágios, mas não o **sombreador de Pixel** estágio para uma das chamadas de desenho.  
  
    > [!NOTE]
    >  Se outros estágios de pipeline — por exemplo, o sombreador hull, sombreador de domínio ou estágios de sombreador de geometria, processar o objeto, qualquer um deles pode ser a causa do problema. Normalmente, o problema está relacionado ao estágio de mais recente em que o resultado não é exibido ou é exibido de forma inesperada.  
  
4.  Pare quando atingir a chamada de desenho que corresponde ao objeto ausente. Nesse cenário, o **estágios de Pipeline gráficos** janela indica que a geometria foi emitida para a GPU \(indicado pela presença do **entrada do Assembler** estágio\) e transformados \(indicado pelo **sombreador de vértices** estágio\), mas não aparece no destino de renderização porque não parece haver um sombreador de pixel active \(indicado pela ausência do **sombreador de Pixel** estágio\). Nesse cenário, você pode até ver a silhueta do objeto ausente no **Output Merger** estágio:  
  
     ![Um evento de DrawIndexed e seu efeito sobre o pipeline](~/debugger/graphics/media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx\_diag\_demo\_misconfigured\_pipeline\_step\_2")  
  
 Depois de confirmar que o aplicativo emitiu uma chamada de desenho de geometria do objeto ausente e descobrir que o estágio de sombreador de pixel estava inativo, você pode examinar o estado do dispositivo para confirmar suas descobertas. Você pode usar o **tabela de objetos gráficos** para examinar o contexto de dispositivo e outros dados de objeto do Direct3D.  
  
#### Para examinar o contexto de dispositivo  
  
1.  Abra o **o contexto de dispositivo d3d11**. No **estágios de Pipeline gráficos** janela, escolha o **ID3D11DeviceContext** link que faz parte do `DrawIndexed` chamada que é exibida na parte superior da janela.  
  
2.  Examine o estado do dispositivo é exibido no **o contexto de dispositivo d3d11** tab para confirmar que nenhum sombreador de pixel estava ativo durante a chamada de desenho. Nesse cenário, o **informações gerais do sombreador**— exibido sob **estado do sombreador de pixel**— indica que o sombreador é **nulo**:  
  
     ![O contexto de dispositivo D3D 11 mostra o estado de sombreador de pixel](~/debugger/graphics/media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx\_diag\_demo\_misconfigured\_pipeline\_step\_4")  
  
 Depois de confirmar que o sombreador de pixel foi definido como null por seu aplicativo, a próxima etapa é encontrar o local no código\-fonte do aplicativo em que o sombreador é definido. Você pode usar o **lista de eventos gráficos** junto com o **pilha de chamadas do evento de gráficos** para encontrar esse local.  
  
#### Para localizar onde o sombreador de pixel é definido no código\-fonte do aplicativo  
  
1.  Encontre o `PSSetShader` chamada que corresponde ao objeto ausente. No **lista de eventos gráficos** janela, digite "desenhado. PSSetShader"no **pesquisa** caixa no canto superior direito do **lista de eventos gráficos** janela. Isso filtra a lista para que ele contém apenas os eventos de "PSSetShader" e que têm "Desenhar" em seus cargos. Escolha o primeiro `PSSetShader` chamada aparece antes da chamada de desenho do objeto ausente.  
  
    > [!NOTE]
    >  `PSSetShader` não aparecerão no **lista de eventos gráficos** janela se ele não foi definido durante esse período. Geralmente isso ocorre apenas se o sombreador de pixel apenas uma é usado para todos os objetos, ou se o `PSSetShader` chamada acidentalmente foi ignorada durante esse período. Em ambos os casos, é recomendável que você pesquise o código\-fonte do aplicativo para `PSSetShader` chamadas e usar técnicas de depuração tradicional para examinar o comportamento dessas chamadas.  
  
2.  Abra o **pilha de chamadas do evento de gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **pilha de chamadas do evento de gráficos**.  
  
3.  Use a pilha de chamadas para localizar o `PSSetShader` chamar no código\-fonte do aplicativo. No **pilha de chamadas do evento de gráficos** janela, escolha a chamada mais alto e examine o valor do sombreador de pixel está sendo definido como. O sombreador de pixel pode ser definido diretamente como null ou o null pode ocorrer devido a um argumento passado para a função ou outro estado. Se ele não é definido diretamente, você poderá localizar a origem do valor nulo em algum lugar para cima a pilha de chamadas. Nesse cenário, você descobre que o sombreador de pixel está sendo definido diretamente para `nullptr` na função principal, que é denominado `CubeRenderer::Render`:  
  
     ![O código que não inicializam o sombreador de pixels](~/debugger/graphics/media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx\_diag\_demo\_misconfigured\_pipeline\_step\_5")  
  
    > [!NOTE]
    >  Se você não conseguir localizar a origem do valor nulo apenas examinando a pilha de chamadas, recomendamos que você defina um ponto de interrupção condicional no `PSSetShader` chamar, que interrompe a execução do programa quando o sombreador de pixel será definido como null. Em seguida, reiniciar o aplicativo no modo de depuração e usar técnicas de depuração tradicionais para localizar a origem do valor nulo.  
  
 Para corrigir o problema, atribua o sombreador de pixel correto usando o primeiro parâmetro do `ID3D11DeviceContext::PSSetShader` chamada à API.  
  
 ![O código&#45;fonte C&#43;&#43; corrigido](~/debugger/graphics/media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx\_diag\_demo\_misconfigured\_pipeline\_step\_6")  
  
 Depois de corrigir o código, você poderá recriá\-lo e executar o aplicativo novamente para verificar se o problema de renderização é resolvido:  
  
 ![O objeto é exibido agora](../debugger/media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx\_diag\_demo\_misconfigured\_pipeline\_resolution")  
  
## Próximas etapas