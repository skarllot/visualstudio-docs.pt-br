---
title: "Instru&#231;&#245;es passo a passo: depurando erros de renderiza&#231;&#227;o devido ao sombreamento | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: depurando erros de renderiza&#231;&#227;o devido ao sombreamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo demonstra como usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Diagnóstico de gráficos para investigar um objeto que é colorido incorretamente devido a um bug de sombreador.  
  
 Este passo a passo demonstra como:  
  
-   Examine o documento de log de gráficos para identificar os pixels que mostram o problema.  
  
-   Use o **histórico de Pixel de gráficos** janela para examinar o estado de pixel mais de perto.  
  
-   Use o **depurador HLSL** para examinar os sombreadores de pixel e vértice.  
  
## Cenário  
 Cor incorreta em objetos normalmente ocorre quando um sombreador de vértices passa um pixel informações do sombreador incorreto ou incompleto.  
  
 Nesse cenário, você adicionou recentemente um objeto ao seu aplicativo, juntamente com o novo vértice e sombreadores de pixel para transformar o objeto e dê a ele uma aparência exclusiva. Quando você executa o aplicativo durante um teste, o objeto será renderizado em preto sólido. Usando o diagnóstico de gráficos, você captura o problema para um log de gráficos para que você pode depurar o aplicativo. O problema parece com isso no aplicativo:  
  
 ![O objeto é processado com cores incorretas.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_problem.png "gfx\_diag\_demo\_render\_error\_shader\_problem")  
  
## Investigação  
 Usando as ferramentas de diagnóstico de gráficos, você pode carregar o documento de log de gráficos para inspecionar os quadros que foram capturados durante o teste.  
  
#### Para examinar um quadro em um log de gráficos  
  
1.  Em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], carregar um log de gráficos que contém um quadro que exibe o modelo ausente. Uma nova janela de documento de log de gráficos aparece no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Na parte superior desta janela é a saída de destino de renderização do quadro selecionado. Na parte inferior é parte de **lista quadro**, que exibe cada quadro capturado como uma imagem em miniatura.  
  
2.  No **lista quadro**, selecione um quadro em que o objeto não tem a aparência correta. O destino de renderização é atualizado para refletir o quadro selecionado. Nesse cenário, os gráficos de log documento janela será semelhante a esta:  
  
     ![Os gráficos registrar o documento no Visual Studio.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_1.png "gfx\_diag\_demo\_render\_error\_shader\_step\_1")  
  
 Depois de selecionar um quadro que demonstra o problema, você pode usar o **histórico de Pixel de gráficos** janela para diagnosticar a ele. O **histórico de Pixel de gráficos** janela mostra os primitivos que poderiam ter tido um efeito em um pixel específico, seus sombreadores e quais seus efeitos sobre o destino de renderização são, em ordem cronológica.  
  
#### Para examinar um pixel  
  
1.  Abra o **histórico de Pixel de gráficos** janela. Sobre o **Diagnóstico de gráficos** barra de ferramentas, escolha **histórico de Pixel**.  
  
2.  Selecione um pixel para examinar. Na janela de documento de log de gráficos, selecione um dos pixels no objeto que é colorido incorretamente:  
  
     ![A seleção de um pixel exibe informações sobre seu histórico.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_2.png "gfx\_diag\_demo\_render\_error\_shader\_step\_2")  
  
     O **histórico de Pixel de gráficos** janela é atualizada para refletir o pixel selecionado. Nesse cenário, o **histórico de Pixel de gráficos** janela tem esta aparência:  
  
     ![O histórico de pixel mostra um evento de DrawIndexed.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_3.png "gfx\_diag\_demo\_render\_error\_shader\_step\_3")  
  
     Observe que o resultado do sombreador de pixel é completamente opaco preto \(0, 0, 0, 1\) e que o **Output Merger** combinado com o **anterior** cor do pixel de forma que o **resultado** também é opaco totalmente preto.  
  
 Depois de examinar um pixel é colorido incorretamente e descobrir que a saída do sombreador de pixel não é a cor esperada, você pode usar o depurador HLSL para examinar o sombreador de pixel e descubra o que aconteceu com a cor do objeto. Você pode usar o depurador HLSL para examinar o estado de HLSL variáveis durante a execução, percorrer o código HLSL e defina pontos de interrupção para ajudá\-lo a diagnosticar o problema.  
  
#### Para examinar o sombreador de pixel  
  
1.  Inicie a depuração do sombreador de pixel. No **histórico de Pixel de gráficos** janela sob o objeto do primitiva, lado **sombreador de Pixel**, escolha o **Iniciar depuração** botão.  
  
2.  Nesse cenário, porque o sombreador de pixel só as passa a cor por meio do sombreador de vértices, é fácil observar que o sombreador de pixel não é a origem do problema.  
  
3.  O ponteiro sobre `input.color`. Observe que seu valor é completamente opaco preto \(0, 0, 0, 1\).  
  
     ![O membro "cor" de "entrada" é indefinido.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_5.png "gfx\_diag\_demo\_render\_error\_shader\_step\_5")  
  
     Nesse cenário, a análise revela que a cor incorreta, provavelmente é o resultado de um sombreador de vértices que não fornece as informações de cor certa para o sombreador de pixel operar em.  
  
 Após ter determinado que o sombreador de vértices provavelmente não está fornecendo a informação certa para o sombreador de pixel, a próxima etapa é examinar o sombreador de vértices.  
  
#### Para examinar o sombreador de vértices  
  
1.  Inicie a depuração o sombreador de vértices. No **histórico de Pixel de gráficos** janela sob o objeto do primitiva, lado **sombreador de vértices**, escolha o **Iniciar depuração** botão.  
  
2.  Localize a estrutura de saída do sombreador de vértices — isso é a entrada para o sombreador de pixel. Nesse cenário, o nome dessa estrutura é `output`. Examinar o código de sombreador de vértice e observe que o `color` membro o `output` estrutura tenha sido explicitamente definida como preto totalmente opaca, talvez como resultado de alguém que está depurando esforços.  
  
3.  Confirme que o membro de cor nunca seja copiado na estrutura de entrada. Porque o valor de `output.color` é definido como preto opaco totalmente antes de `output` estrutura é retornada, é uma boa idéia para certificar\-se de que o valor de `output` não foi inicializado corretamente em uma linha anterior. Percorrer o código de sombreador de vértice até alcançar a linha que define `output.color` para preto, enquanto você observa que o valor de `output.color`. Observe que o valor de `output.color` não foi inicializado até que ele seja definido para preto. Isso confirma que a linha de código que define `output.color` para preto deve ser modificado, em vez de excluído.  
  
     ![O valor de "output.color" nunca será inicializado.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_7.png "gfx\_diag\_demo\_render\_error\_shader\_step\_7")  
  
 Depois de determinar que a causa do problema de renderização é que o sombreador de vértices não fornece o valor da cor correta para o sombreador de pixel, você pode usar essas informações para corrigir o problema. Nesse cenário, você pode corrigi\-lo alterando o seguinte código no sombreador de vértices  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 para  
  
```hlsl  
output.color = input.color;  
```  
  
 Esse código simplesmente passa a cor de vértice por meio de vértices do objeto sem modificações — sombreadores de vértices mais complexos poderia modificar a cor antes de passá\-lo por meio de. O código de sombreador de vértice corrigido deve ter esta aparência:  
  
 ![O código de sombreador de vértices corrigido.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_step_8.png "gfx\_diag\_demo\_render\_error\_shader\_step\_8")  
  
 Depois de corrigir o código, recompilá\-lo e executar o aplicativo novamente para descobrir o que é resolvido o problema de renderização.  
  
 ![O objeto é processado com as cores corretas.](~/docs/debugger/graphics/media/gfx_diag_demo_render_error_shader_resolution.png "gfx\_diag\_demo\_render\_error\_shader\_resolution")