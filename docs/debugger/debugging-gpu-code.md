---
title: "Depurando c&#243;digo de GPU | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando c&#243;digo de GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode depurar código C\+\+ que está sendo executado na unidade de processamento gráfico \(GPU\).  O suporte à depuração de GPU no Visual Studio inclui a detecção de concorrência, início de processos e anexação a eles, e a integração nas janelas de depuração.  
  
## Plataformas com suporte  
 A depuração tem suporte no [!INCLUDE[win7](../debugger/includes/win7_md.md)], no [!INCLUDE[win8](../debugger/includes/win8_md.md)], no [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)] e no [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)].  Para depurar no emulador de software, é necessário o [!INCLUDE[win8](../debugger/includes/win8_md.md)] ou [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)].  Para depurar no hardware, você deve instalar os drivers para a sua placa gráfica.  Nem todos os fornecedores de hardware implementam todos os recursos do depurador.  Consulte a documentação do fornecedor para conhecer as restrições.  
  
> [!NOTE]
>  Fornecedores de hardware independentes que desejam oferecer suporte à depuração de GPU no Visual Studio devem criar uma DLL que implementa a interface do VSD3DDebug e destinam\-se a seus próprios drivers.  
  
## Configurando a depuração de GPU  
 O depurador não pode interromper no código de CPU e no código de GPU na mesma execução do aplicativo.  Por padrão, o depurador será interrompido no código da CPU.  Para depurar o código de GPU, use uma destas duas etapas:  
  
-   Na lista **Tipo de Depuração** na barra de ferramentas **Padrão**, escolha **Somente GPU**.  
  
-   No **Gerenciador de Soluções**, no menu de atalho do projeto, selecione **Propriedades**.  Na caixa de diálogo **Páginas de Propriedades**, selecione **Depuração** e **Somente GPU** na lista **Tipo de Depurador**.  
  
## Iniciando e anexando a aplicativos  
 Você pode usar os comandos de depuração do Visual Studio para iniciar e interromper a depuração de GPU.  Para obter mais informações, consulte [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md).  Você também pode anexar o depurador de GPU a um processo em execução, mas somente se esse processo executar o código de GPU.  Para obter mais informações, consulte [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Executar o bloco atual até o cursor e executar até o cursor  
 Quando você estiver depurando no GPU, terá duas opções para executar até o local do cursor.  Os comandos para as duas opções estão disponíveis no menu de atalho do editor de códigos.  
  
1.  O comando **Executar até o Cursor** executa seu aplicativo até alcançar o local do cursor e, em seguida, é interrompido.  Isso não significa que o thread atual é executado até o cursor; significa que o primeiro thread que alcançar o ponto do cursor dispara a interrupção.  Consulte [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)  
  
2.  O comando **Executar Bloco Atual até o Cursor** executa seu aplicativo até que todos os threads no bloco atual atinjam o cursor e, em seguida, seja interrompido.  
  
## Janelas de depuração  
 Ao usar determinadas janelas de depuração, você pode examinar, sinalizar e congelar threads de GPU.  Para obter mais informações, consulte:  
  
-   [Usando a janela Pilhas Paralelas](../debugger/using-the-parallel-stacks-window.md)  
  
-   [Usando a janela Tarefas](../debugger/using-the-tasks-window.md)  
  
-   [Como usar a janela Inspeção Paralela](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [Depurar threads e processos](../debugger/debug-threads-and-processes.md) \(Barra de ferramentas Local de Depuração\)  
  
-   [Como usar a janela Threads de GPU](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
  
## Exceções de sincronização de dados  
 O depurador pode identificar várias condições de sincronização de dados durante a execução.  Quando uma condição for detectada, o depurador entrará no estado de interrupção.  Você tem duas opções: **Interromper** ou **Continuar**.  Usando a caixa de diálogo **Exceções**, você pode configurar se o depurador detecta essas condições e também para quais condições ele interromperá.  Para obter mais informações, consulte [Gerenciando exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md).  Você também pode usar a caixa de diálogo **Opções** para especificar que o depurador deve ignorar exceções se os dados que são gravados não alterarem o valor dos dados.  Para obter mais informações, consulte [Caixa de diálogo Geral, Depuração, Opções](../debugger/general-debugging-options-dialog-box.md).  
  
## Solução de problemas  
  
### Especificando um acelerador  
 Os pontos de interrupção no código de GPU serão atingidos apenas se o código estiver em execução no acelerador [accelerator::direct3d\_ref](../Topic/accelerator::direct3d_ref%20Data%20Member.md) \(REF\).  Se você não especificar um acelerador em seu código, o acelerador REF será selecionado automaticamente como o **Tipo de Acelerador de Depuração** nas propriedades do projeto.  Se seu código selecionar explicitamente um acelerador, o acelerador REF não será usado durante a depuração e os pontos de interrupção não serão atingidos a menos que seu hardware de GPU tiver suporte à depuração.  Você pode solucionar isso escrevendo seu código de forma que use um acelerador REF durante a depuração.  Para obter mais informações, consulte as propriedades de projeto e [Usando objetos accelerator e accelerator\_view](/visual-cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) e [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Pontos de interrupção condicionais  
 Os pontos de interrupção condicionais no código de GPU têm suporte, mas nem todas as expressões podem ser avaliadas no dispositivo.  Quando uma expressão não pode ser avaliada no dispositivo, ela será avaliada no depurador.  O depurador provavelmente será executado com mais lentidão do que no dispositivo.  
  
### Erro: problema de configuração no Tipo de Acelerador de Depuração.  
 Esse erro ocorre quando há uma inconsistência entre as configurações de projeto e a configuração do PC no qual você está depurando.  Para obter mais informações, consulte [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Erro: o driver de depuração do Tipo de Acelerador de Depuração selecionado não está instalado no computador de destino.  
 Esse erro ocorrerá se você estiver depurando em um PC remoto.  O depurador não poderá determinar até o tempo de execução se os drivers estiverem instalados no PC remoto.  Os drivers estão disponíveis com o fabricante da placa gráfica.  
  
### Erro: a TDR \(Detecção de Tempo Limite e Recuperação\) deve ser desabilitada no site remoto.  
 É possível que as computações de C\+\+ AMP excedam o intervalo de tempo padrão que é definido pela detecção de tempo limite do Windows e pelo processo de recuperação \(TDR\).  Quando isso acontecer, a computação será cancelada e os dados serão perdidos.  Para obter mais informações, consulte [Manipulando TDRs em C\+\+ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154).  
  
## Consulte também  
 [Instruções passo a passo: depurando um aplicativo C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)   
 [Definições do projeto para uma configuração de depuração do C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Iniciar a depuração de GPU no Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=255381)