---
title: "Como depurar o c&#243;digo otimizado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "pontos de interrupção, em código otimizado"
  - "depurar compilações, otimizando"
  - "depurando [C++], código otimizado"
  - "otimização, depurar compilações"
  - "código otimizado, depuração"
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar o c&#243;digo otimizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem diferir das descritas no Help dependendo de suas configurações ativas ou de edição.  Para alterar as configurações, escolha Importar e exportar configurações no menu Ferramentas.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
>  O [\/Zo \(Enhance Optimized Debugging\)](/visual-cpp/build/reference/zo-enhance-optimized-debugging)opção de compilador \(introduzida no Visual Studio atualização 3\) gera informações de depuração mais avançadas para código otimizado \(projetos que não são criados com o **\/Od** opção de compilador.  Consulte [\/O opções \(otimizar código\)](/visual-cpp/build/reference/o-options-optimize-code)\).  Isso inclui suporte aperfeiçoado para depuração de funções embutidas e variáveis locais.  
>   
>  [Editar e continuar](../debugger/edit-and-continue-visual-csharp.md) é desabilitado quando o **\/zo \*** ocompiler opção é usada.  
  
 Quando o compilador otimiza o código, ele reposiciona e reclassifica instruções.  Isso resulta em um código compilado mais eficiente.  Devido a esse rearranjo, o depurador nem sempre pode identificar o código\-fonte que corresponde a um conjunto de instruções.  
  
 A otimização pode afetar:  
  
-   As variáveis locais, que podem ser removidas pelo otimizador ou movidas para locais que o depurador não entende.  
  
-   Posições dentro de uma função, que são alteradas quando o otimizador mescla blocos de código.  
  
-   Nomes de função para quadros na pilha de chamadas, que pode estar errado se o otimizador mesclar duas funções.  
  
 Os quadros que você vê na pilha de chamadas estão quase sempre corretos, porém, supondo que você tenha símbolos para todos os quadros.  Os quadros na pilha de chamadas estarão incorretos se você tiver um dano na pilha, se você tiver as funções escritas na linguagem assembly, ou se houver quadros do sistema operacional sem símbolos correspondentes na pilha de chamadas.  
  
 As variáveis globais e estáticas são sempre mostradas corretamente.  Da mesma forma que o layout da estrutura.  Se você tiver um ponteiro para uma estrutura e o valor do ponteiro estiver correto, cada variável de membro da estrutura mostrará o valor correto.  
  
 Devido a essas restrições, você deverá depurar usando uma versão não otimizada do programa se isso for possível.  Por padrão, a otimização está desativada na configuração de Depuração de um programa do Visual C\+\+ e ativada na configuração de Versão.  
  
 No entanto, um bug pode aparecer somente em uma versão otimizada de um programa.  Nesse caso, você deverá depurar o código otimizado.  
  
### Para ativar a otimização em uma configuração da compilação de Depuração  
  
1.  Quando você cria um novo projeto, selecione o destino de `Win32 Debug`.  Use o `Win32``Debug` de destino até que o programa seja depurado completamente e você está pronto para criar um `Win32 Release` destino.  O compilador não otimiza o destino de `Win32 Debug`.  
  
2.  Selecione o projeto no Gerenciador de Soluções.  
  
3.  No menu **Exibir**, clique em **Páginas de Propriedades**.  
  
4.  Na caixa de diálogo **Páginas de Propriedades**, verifique se `Debug` está selecionado na lista suspensa **Configuração**.  
  
5.  Na exibição da pasta à esquerda, selecione a pasta **C\/C\+\+**.  
  
6.  Na pasta **C\+\+**, selecione `Optimization`.  
  
7.  Na lista de propriedades à direita, localize `Optimization`.  A configuração ao lado provavelmente informa `Disabled (`[\/Od](/visual-cpp/build/reference/od-disable-debug)`)`.  Choose one of the other options \(`Minimum Size``(`[\/O1](/visual-cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(`[\/O2](/visual-cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(`[\/Ox](/visual-cpp/build/reference/ox-full-optimization)`)`, or `Custom`\).  
  
8.  Se você escolher a opção `Custom` para `Optimization`, agora poderá definir opções para qualquer uma das outras propriedades mostradas na lista de propriedades.  
  
9. Selecione as propriedades de configuração, C\/C\+\+, nó de linha de comando de página de propriedades do projeto e adicionar `(`[\/zo \*](/visual-cpp/build/reference/zo-enhance-optimized-debugging)`)` para o **Opções adicionais** caixa de texto.  
  
    > [!WARNING]
    >  `/Zo` requer o Visual Studio 2013 atualização 3 ou posterior.  
    >   
    >  Adicionando `/Zo` desabilitará [Editar e continuar](../debugger/edit-and-continue-visual-csharp.md).  
  
 Quando você depura o código otimizado, use a janela **Desmontagem** para ver quais instruções de fato estão criadas e executadas.  Quando você define pontos de interrupção, precisa saber que o ponto de interrupção pode mover junto com uma instrução.  Por exemplo, considere o seguinte código:  
  
```  
for (x=0; x<10; x++)  
```  
  
 Suponha que você defina um ponto de interrupção nesta linha.  Você pode esperar que o ponto de interrupção seja atingido 10 vezes, mas se o código for otimizado, o ponto de interrupção será atingido somente uma vez.  Isso ocorre porque a primeira instrução define o valor de `x` como 0.  O compilador reconhece que isso somente precisa ser feito uma vez e o move para fora do loop.  O ponto de interrupção também será movido.  As instruções que comparam e incrementam `x` permanecem dentro do loop.  Quando você exibe a janela **Desmontagem**, a [unidade da etapa](http://msdn.microsoft.com/pt-br/8791dac9-64d1-4bb9-b59e-8d59af1833f9) será definida automaticamente como Instrução para obter maior controle, o que é útil quando você depura código otimizado.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)