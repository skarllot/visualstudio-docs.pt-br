---
title: "Instru&#231;&#245;es passo a passo: depurando um aplicativo paralelo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
helpviewer_keywords: 
  - "depurador, explicações passo a passo de tarefas paralelas"
  - "depuração, aplicativos paralelos"
  - "aplicativos paralelos, depurando [C#]"
  - "aplicativos paralelos, depurando [C++]"
  - "aplicativos paralelos, depurando [Visual Basic]"
  - "janela de ferramenta de pilhas paralelas"
  - "janela de tarefas paralelas"
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: depurando um aplicativo paralelo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este passo a passo descreve como usar as janelas **Tarefas Paralelas** e **Pilhas Paralelas** para depurar um aplicativo paralelo.  Essas janelas ajudam a compreender e a verificar o comportamento em tempo de execução do código que usa [Biblioteca de tarefas paralelas \(TPL\)](../Topic/Task%20Parallel%20Library%20\(TPL\).md) ou [Tempo de Execução de Simultaneidade](/visual-cpp/parallel/concrt/concurrency-runtime).  Este passo a passo fornece código de exemplo que tem pontos de interrupção internos.  Após a interrupção do código, este passo a passo mostra como usar as janelas **Tarefas Paralelas** e **Pilhas Paralelas** para examiná\-lo.  
  
 Este passo a passo ensina estas tarefas:  
  
-   Como exibir as chamadas de pilhas de todos os threads em uma exibição.  
  
-   Como exibir a lista de instâncias de `System.Threading.Tasks.Task` que são criadas no seu aplicativo.  
  
-   Como exibir as chamadas de pilhas de tarefas reais em vez de threads.  
  
-   Como navegar até o código a partir das janelas **Tarefas Paralelas** e **Pilhas Paralelas**.  
  
-   Como as janelas lidam com a escala por agrupamento, zoom e outros recursos relacionados.  
  
## Pré-requisitos  
 Este passo a passo pressupõe que **Apenas Meu Código** está habilitado.  No menu **Ferramentas**, clique em **Opções**, expanda o nó **Depuração**, selecione **Geral** e **Habilitar Apenas Meu Código \(Gerenciado Somente\)**.  Se você não definir esse recurso, ainda poderá usar este passo a passo, mas os resultados poderão ser diferentes das ilustrações.  
  
## Exemplo do C\#  
 Se você usar o exemplo do C\#, este passo a passo também pressuporá que o código externo está oculto.  Para ativar ou desativar a exibição do código externo, clique com o botão direito do mouse no cabeçalho da tabela **Nome** da janela **Pilha de Chamadas** e marque ou desmarque **Mostrar Código Externo**.  Se você não definir esse recurso, ainda poderá usar este passo a passo, mas os resultados poderão ser diferentes das ilustrações.  
  
## Exemplo do C\+\+  
 Se você usar o exemplo do C\+\+, poderá ignorar referências ao código externo neste tópico.  O código externo aplica\-se somente ao exemplo do C\#.  
  
## Ilustrações  
 As ilustrações neste tópico foram gravadas em um computador de quatro núcleos executando o exemplo do C\#.  Embora você possa usar outras configurações para concluir este passo a passo, as ilustrações poderão diferir do que é exibido em seu computador.  
  
## Criando o projeto de exemplo  
 O código de exemplo neste passo a passo é para um aplicativo que não faça nada.  O objetivo é apenas entender como usar as janelas de ferramenta para depurar um aplicativo paralelo.  
  
#### Para criar o projeto de exemplo  
  
1.  No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  No painel **Modelos Instalados**, selecione Visual C \#, Visual Basic ou Visual C\+\+.  Para as linguagens gerenciadas, certifique\-se de que [!INCLUDE[net_v40_short](../debugger/includes/net_v40_short_md.md)] seja exibido na caixa da estrutura.  
  
3.  Selecione **Aplicativo de Console** e clique em **OK**.  Permaneça na configuração de depuração, que é o padrão.  
  
4.  No projeto, abra o arquivo de código .cpp, .cs ou .vb.  Exclua o conteúdo para criar um arquivo de código vazio.  
  
5.  Cole o código a seguir para seu idioma escolhido no arquivo de código vazio.  
  
 [!code-cs[Debugger#1](../debugger/codesnippet/CSharp/walkthrough-debugging-a-parallel-application_1.cs)]
 [!code-cpp[Debugger#1](../debugger/codesnippet/CPP/walkthrough-debugging-a-parallel-application_1.cpp)]
 [!code-vb[Debugger#1](../debugger/codesnippet/VisualBasic/walkthrough-debugging-a-parallel-application_1.vb)]  
  
1.  No menu **Arquivo**, clique em **Salvar Tudo**.  
  
2.  No menu **Compilação**, clique em **Recompilar Solução**.  
  
     Observe que há quatro chamadas a `Debugger.Break` \(`DebugBreak` no exemplo do C\+\+\). Em virtude disso, você não precisa inserir pontos de interrupção; a execução do aplicativo causará sua interrupção no depurador até quatro vezes.  
  
## Usando a janela Pilhas Paralelas: exibição de Threads  
 No menu **Depuração**, clique em **Iniciar Depuração**.  Aguarde até que o primeiro ponto de interrupção seja atingido.  
  
#### Para exibir a pilha de chamadas de um único thread  
  
1.  No menu **Depurar**, aponte para **Windows** e clique em **Threads**.  Encaixe a janela **Threads** na parte inferior do Visual Studio.  
  
2.  No menu **Depurar**, aponte para **Windows** e clique em **Pilha de Chamadas**.  Encaixe a janela **Pilha de Chamadas** na parte inferior do Visual Studio.  
  
3.  Clique duas vezes em um thread na janela **Threads** para torná\-lo atual.  Os threads atuais têm uma seta amarela.  Quando você altera o thread atual, a pilha de chamadas é exibida na janela **Pilha de Chamadas**.  
  
#### Para examinar a janela Pilhas Paralelas  
  
1.  No menu **Depurar**, aponte para **Windows** e clique em **Pilhas Paralelas**.  Verifique se **Threads** está selecionado na caixa no canto superior esquerdo.  
  
     Usando a janela **Pilhas Paralelas** , você pode exibir várias pilhas de chamadas ao mesmo tempo em uma exibição.  A ilustração a seguir mostra a janela **Pilhas Paralelas** acima da janela **Pilha de Chamadas**.  
  
     ![Janela pilhas paralelas na exibição de Threads](~/debugger/media/pdb_walkthrough_1.png "PDB\_Walkthrough\_1")  
  
     A pilha de chamadas do thread principal é exibida em uma caixa e as pilhas de chamadas dos outros quatro threads são agrupadas em outra caixa.  Quatro threads são agrupados porque os quadros de pilhas compartilham os mesmos contextos do método; isto é, estão nos mesmos métodos: `A`, `B`, e `C`.  Para exibir as IDs de thread e os nomes dos threads que compartilham a mesma caixa, passe o mouse sobre o cabeçalho \(**4 Threads**\).  O thread atual é exibido em negrito, como mostra a ilustração a seguir.  
  
     ![Dica de ferramenta com nomes e identificações de segmento](~/debugger/media/pdb_walkthrough_1a.png "PDB\_Walkthrough\_1A")  
  
     A seta amarela indica o quadro de pilhas do thread atual.  Para obter mais informações, passe o mouse sobre ela  
  
     ![Dica de ferramenta no quadro de pilha ativa](~/debugger/media/pdb_walkthrough_1b.png "PDB\_Walkthrough\_1B")  
  
     Você pode definir o nível de detalhes que deseja mostrar dos registros de ativação \(**Nomes de Módulo**, **Tipos de Parâmetro**, **Nomes de Parâmetros**, **Valores de Parâmetro**, **Números de Linha** e **Deslocamentos de Byte**\) clicando com o botão direito do mouse na janela **Pilha de Chamadas**.  
  
     Um realce azul ao redor de uma caixa indica que o thread atual é parte dessa caixa.  O thread atual também é indicado pelo registro de ativação em negrito na dica de ferramenta.  Se você clicar duas vezes no thread principal na janela Threads, poderá observar que o realce azul na janela **Pilhas Paralelas** se move também.  
  
     ![Pilhas de thread principal realçado em azul](~/debugger/media/pdb_walkthrough_1c.png "PDB\_Walkthrough\_1C")  
  
#### Para retomar a execução até o segundo ponto de interrupção  
  
1.  Para retomar a execução até atingir o segundo ponto de interrupção, no menu **Depurar**, clique em **Continuar**.  A ilustração a seguir mostra a árvore do thread no segundo ponto de interrupção.  
  
     ![Janela pilhas paralelas com muitas ramificações](~/debugger/media/pdb_walkthrough_2.png "PDB\_Walkthrough\_2")  
  
     No primeiro ponto de interrupção, quatro threads foram de S.A para S.B até o método S.C.  Essas informações ainda estão visíveis na janela **Pilhas Paralelas**, mas os quatro threads progrediram mais.  Um deles continuou até S.D e depois S.E.  Outro continuou até S.F, S.G e S.H.  Dois outros continuaram até S.I e S.J, e um deles foi até S.K e o outro continuou até o código externo de não usuário.  
  
     Você pode passar o mouse sobre o cabeçalho da caixa, por exemplo, **1 Thread** ou **2 Threads**, para ver as IDs dos threads.  Você pode passar o mouse sobre registros de ativação para consultar as IDs de thread e outros detalhes do registro.  O realce azul indica o thread atual e a seta amarela indica o registro de ativação ativo do thread atual.  
  
     O ícone de pano\-threads \(sobrepondo linhas onduladas azuis e vermelhas\) indica os registros de ativação ativos dos threads não atuais.  Na janela **Pilha de Chamadas**, clique duas vezes em S.B para trocar de registros.  A janela **Pilhas Paralelas** indica o registro de ativação atual do thread atual usando um ícone de seta curva verde.  
  
     Na janela **Threads**, alterne entre threads e observe que a exibição na janela **Pilhas Paralelas** é atualizada.  
  
     Você pode alternar para outro thread ou para outro registro de outro thread, usando o menu de atalho na janela **Pilhas Paralelas**.  Por exemplo, clique com o botão direito do mouse em S.J, aponte para **Alternar para Quadro** e clique em um comando.  
  
     ![Caminho de pilhas paralelas de execução](~/debugger/media/pdb_walkthrough_2b.png "PDB\_Walkthrough\_2B")  
  
     Clique com o botão direito do mouse em S.C e aponte para **Alternar para Quadro**.  Um dos comandos tem uma marca de seleção que indica o registro de ativação do thread atual.  Você pode alternar para esse registro do mesmo thread \(apenas a seta verde se moverá\) ou pode alternar para o outro thread \(o realce azul também se moverá\).  A ilustração a seguir mostra o submenu.  
  
     ![Menu pilhas com 2 opções em C, embora J seja o atual](~/debugger/media/pdb_walkthrough_3.png "PDB\_Walkthrough\_3")  
  
     Quando um contexto de método é associado a apenas um registro de ativação, o cabeçalho da caixa exibe **1 Thread** e você pode alternar clicando duas vezes nele.  Se você clicar duas vezes em um contexto de método que tenha mais de 1 registro associado a ele, o menu será exibido automaticamente.  Enquanto você passa o mouse sobre os contextos de método, observe o triângulo preto no lado direito.  Um clique nesse triângulo também exibe o menu de atalho.  
  
     Para os aplicativos grandes que têm muitos threads, talvez seja conveniente se concentrar apenas em um subconjunto de threads.  A janela **Pilhas Paralelas** pode exibir pilhas de chamadas apenas para threads sinalizados.  Na barra de ferramentas, clique no botão **Mostrar Somente Sinalizados** ao lado da caixa de listagem.  
  
     ![Janela pilhas vazias e dica de ferramenta](~/debugger/media/pdb_walkthrough_3a.png "PDB\_Walkthrough\_3A")  
  
     Em seguida, na janela **Threads**, sinalize threads individualmente para ver como as respectivas pilhas de chamadas aparecem na janela **Pilhas Paralelas**.  Para sinalizar threads, use o menu de atalho ou a primeira célula de um thread.  Clique no botão de barra de ferramentas **Mostrar Somente Sinalizados** novamente para mostrar todos os threads.  
  
#### Para retomar a execução até o terceiro ponto de interrupção  
  
1.  Para retomar a execução até atingir o terceiro ponto de interrupção, no menu **Depurar**, clique em **Continuar**.  
  
     Quando vários threads estão no mesmo método, mas o método não estava no início da pilha de chamadas, ele é exibido em caixas diferentes.  Um exemplo no ponto de interrupção atual é S.L, que tem três threads e aparece em três caixas.  Clique duas vezes em S.L.  
  
     ![Caminho de execução de pilhas paralelas](~/debugger/media/pdb_walkthrough_3b.png "PDB\_Walkthrough\_3B")  
  
     Observe que S.L está em negrito nas outras duas caixas para que você possa ver onde mais ele aparece.  Para saber quais registros chamam S.L e quais registros ele chama, clique no botão **Ativar\/Desativar Modo de Exibição do Método** na barra de ferramentas.  A ilustração a seguir mostra o modo de exibição do método da janela **Pilhas Paralelas** .  
  
     ![Janela pilhas na exibição de método](~/debugger/media/pdw_walkthrough_4.png "PDW\_Walkthrough\_4")  
  
     Observe como o diagrama girou no método selecionado e o posicionou em sua própria caixa no meio da exibição.  Os receptores e os chamadores aparecem nas partes superior e inferior.  Clique no botão **Ativar\/Desativar Modo de Exibição do Método** novamente para sair desse modo.  
  
     O menu de atalho da janela **Pilhas Paralelas** também tem os seguintes itens.  
  
    -   **Exibição Hexadecimal** alterna os números decimais e hexadecimais nas dicas de ferramenta.  
  
    -   **Informações de Carregamento de Símbolos** e **Configurações de Símbolo** abrem as respectivas caixas de diálogo.  
  
    -   **Ir para Código\-Fonte** e **Ir para Desmontagem** navegam no editor até o método selecionado.  
  
    -   **Mostrar Código Externo** exibe todos os registros mesmo se não estiverem no código do usuário.  Tente verificar o diagrama se expande para acomodar os registros adicionais \(que podem ser escurecidos porque você não tem símbolos para eles\).  
  
     Quando houver diagramas grandes e você for para o próximo ponto de interrupção, talvez seja conveniente que o modo de exibição role até o registro de ativação ativo do thread atual; isto é, o thread que atingiu o ponto de interrupção primeiro.  Na janela **Pilhas Paralelas**, verifique se o botão **Autorrolagem para Quadro de Pilha Atual** na barra de ferramentas está ativo.  
  
     ![Autorrolagem na janela pilhas paralelas](~/debugger/media/pdb_walkthrough_4a.png "PDB\_Walkthrough\_4A")  
  
2.  Antes de continuar, na janela **Pilhas Paralelas**, role até a extrema esquerda e até o fim.  
  
#### Para retomar a execução até o quarto ponto de interrupção  
  
1.  Para retomar a execução até atingir o quarto ponto de interrupção, no menu **Depurar**, clique em **Continuar**.  
  
     Observe como o modo de exibição rolou automaticamente até o local certo.  Alterne os threads na janela **Threads** ou alterne registros de ativação na janela **Pilha de Chamadas** e observe como o modo de exibição rola automaticamente sempre até o registro correto.  Desative a opção **Autorrolagem até Quadro de Ferramenta atual** e veja a diferença.  
  
     O **Modo de Exibição Vista de Pássaro** também é útil com diagramas grandes na janela **Pilhas Paralelas**.  Você pode ver o **Modo de Exibição de Vista de Pássaro** clicando no botão entre as barras de rolagem no canto inferior direito da janela, como mostra a ilustração a seguir.  
  
     ![Janela pilhas paralelas com exibição de vista aérea](~/debugger/media/pdb_walkthrough_5.png "PDB\_Walkthrough\_5")  
  
     Você pode mover o retângulo para ver uma rápida panorâmica do diagrama.  
  
     Outra maneira de mover o diagrama em qualquer direção é clicar em uma área em branco do diagrama e arrastá\-la até onde desejar.  
  
     Para ampliar ou reduzir o diagrama, mantenha pressionada a tecla CTRL enquanto move a roda do mouse.  Como alternativa, clique no botão Aplicar Zoom na barra de ferramentas e use a ferramenta Zoom.  
  
     ![Pilhas lado a lado Zoom in e check&#45;out](~/debugger/media/pdb_walkthrough_5a.png "PDB\_Walkthrough\_5A")  
  
     Você também pode exibir as pilhas na direção de cima para baixo em vez de baixo para cima, clicando no menu **Ferramentas** e em **Opções** e selecionando ou desmarcando a opção no nó **Depuração**.  
  
2.  Antes de continuar, no menu **Depurar**, clique em **Parar Depuração** para terminar a execução.  
  
## Usando a janela Tarefas Paralelas e o Modo de Exibição Tarefas na janela Pilhas Paralelas  
 Recomendamos que você conclua os procedimentos anteriores antes de continuar.  
  
#### Para reiniciar o aplicativo até atingir o primeiro ponto de interrupção  
  
1.  No menu **Depurar**, clique em **Iniciar Depuração** e aguarde até que o primeiro ponto de interrupção seja atingido.  
  
2.  No menu **Depurar**, aponte para **Windows** e clique em **Threads**.  Encaixe a janela **Threads** na parte inferior do Visual Studio.  
  
3.  No menu **Depurar**, aponte para **Windows** e clique em **Pilha de Chamadas**.  Encaixe a janela **Pilha de Chamadas** na parte inferior do Visual Studio.  
  
4.  Clique duas vezes em um thread na janela **Threads** para torná\-lo atual.  Os threads atuais têm a seta amarela.  Quando você altera o thread atual, as outras janelas são atualizadas.  Em seguida, examinaremos tarefas.  
  
5.  No menu **Depurar**, aponte para **Windows** e clique em **Tarefas Paralelas**.  A ilustração a seguir mostra a janela **Tarefas Paralelas**.  
  
     ![Janela tarefas paralelas com 4 tarefas em execução](~/debugger/media/pdw_walkthrough_6.png "PDW\_Walkthrough\_6")  
  
     Para cada tarefa em execução, você pode ler a ID, que é retornada pela propriedade do mesmo nome, a ID e o nome do thread que a executa, seu local \(passar o mouse sobre ele exibe uma dica de ferramenta que tem a pilha de chamadas inteira\).  Além disso, na coluna **Tarefa**, você pode ver o método que foi passado na tarefa; em outras palavras, o ponto de partida.  
  
     Você pode classificar qualquer coluna.  Observe o glifo de classificação que indica a coluna e a direção de classificação.  Também é possível reorganizar as colunas arrastando\-as para a esquerda ou a direita.  
  
     A seta amarela indica a tarefa atual.  Você pode alternar tarefas clicando duas vezes em uma tarefa ou usando o menu de atalho.  Quando você alterna tarefas, o thread subjacente se torna o atual e as outras janelas são atualizadas.  
  
     Quando você alterna manualmente de uma tarefa para outra, a seta amarela se move, mas uma seta branca ainda mostra a tarefa que causou a interrupção do depurador.  
  
#### Para retomar a execução até o segundo ponto de interrupção  
  
1.  Para retomar a execução até atingir o segundo ponto de interrupção, no menu **Depurar**, clique em **Continuar**.  
  
     Anteriormente, a coluna **Status** mostrava todas as tarefas como Em Execução, mas agora duas tarefas estão Aguardando.  As tarefas podem ser bloqueadas por diversos motivos diferentes.  Na coluna **Status**, passe o mouse sobre uma tarefa em espera para saber porque ela está bloqueada.  Por exemplo, na ilustração, a tarefa 3 está aguardando a tarefa 4.  
  
     ![Janela tarefas paralelas com 2 tarefas em espera](~/debugger/media/pdb_walkthrough_7.png "PDB\_Walkthrough\_7")  
  
     A tarefa 4, por sua vez, está aguardando um monitor de propriedade do thread atribuído à tarefa 2.  
  
     ![Janela tarefas com tarefa em espera e dica de ferramenta](~/debugger/media/pdb_walkthrough_7a.png "PDB\_Walkthrough\_7A")  
  
     Você pode sinalizar uma tarefa clicando no sinalizador na primeira coluna da janela **Tarefas Paralelas**.  
  
     Você pode usar a sinalização para controlar tarefas entre pontos de interrupção diferentes na mesma sessão de depuração ou para filtrar as tarefas cujas pilhas de chamadas são mostradas na janela **Pilhas Paralelas**.  
  
     Quando você usou a janela **Pilhas Paralelas** antes, exibiu os threads do aplicativo.  Exiba a janela **Pilhas Paralelas** novamente, mas desta vez, exiba as tarefas do aplicativo.  Para fazer isso, selecione **Tarefas** na caixa na parte superior esquerda.  A ilustração a seguir mostra o Modo de Exibição de Tarefas.  
  
     ![Janela tarefas paralelas na exibição de tarefas](~/debugger/media/pdb_walkthrough_8.png "PDB\_Walkthrough\_8")  
  
     Os threads que não estão executando tarefas no momento não são mostrados no Modo de Exibição de Tarefas da janela **Pilhas Paralelas**.  Além disso, para os threads que executam tarefas, alguns registros de ativação que não são relevantes para tarefas são filtrados das partes superior e inferior da pilha.  
  
     Exiba a janela **Tarefas Paralelas** novamente.  Clique com o botão direito do mouse em qualquer cabeçalho de coluna para ver um menu de atalho da coluna.  
  
     ![Menu de columnheader tarefas paralelas](~/debugger/media/pdb_walkthrough_8a.png "PDB\_Walkthrough\_8A")  
  
     Você pode usar o menu de atalho para adicionar ou remover colunas.  Por exemplo, a coluna Appdomain não está selecionada; consequentemente, não é exibida na lista.  Clique em **Pai**.  A coluna **Pai** aparece sem valores para todas as quatro tarefas.  
  
#### Para retomar a execução até o terceiro ponto de interrupção  
  
1.  Para retomar a execução até atingir o terceiro ponto de interrupção, no menu **Depurar**, clique em **Continuar**.  
  
     Uma nova tarefa, tarefa 5, está sendo executada e a tarefa 4 está aguardando.  Você pode ver porque passando o cursor do mouse sobre a tarefa em espera na janela **Status**.  Na coluna **Pai** , observe que a tarefa 4 é o pai da tarefa 5.  
  
     Para visualizar melhor a relação pai\-filho, clique com o botão direito do mouse no cabeçalho da coluna **Pai** e clique em **Modo de Exibição Pai\-Filho**.  Você verá a ilustração a seguir.  
  
     ![Modo de exibição de tarefas paralelo na exibição pai&#45;filho](~/debugger/media/pdb_walkthrough_9.png "PDB\_Walkthrough\_9")  
  
     Observe que as tarefas 4 e 5 estão em execução no mesmo thread.  Essas informações não são exibidas na janela **Threads**; sua exibição é outro benefício da janela **Tarefas Paralelas**.  Para confirmar isso, exiba a janela **Pilhas Paralelas**.  Verifique se você está exibindo **Tarefas**.  Localize as tarefas 4 e 5 clicando duas vezes nelas na janela **Tarefas Paralelas**.  Quando fizer isso, o realce azul na janela **Pilhas Paralelas** será atualizado.  Você também pode localizar as tarefas 4 e 5 revisando as dicas de ferramenta na janela **Pilhas Paralelas**.  
  
     ![Janela pilhas paralelas na exibição de tarefas](~/debugger/media/pdb_walkthrough_9a.png "PDB\_Walkthrough\_9A")  
  
     Na janela **Pilhas Paralelas**, clique com o botão direito do mouse em S.P e clique em **Ir para Thread**.  A janela alterna para o Modo de Exibição de Threads e o registro correspondente está na exibição.  Você pode ver as duas tarefas no mesmo thread.  
  
     ![Exibição de threads com thread realçado](~/debugger/media/pdb_walkthrough_9b.png "PDB\_Walkthrough\_9B")  
  
     Esse é outro benefício do Modo de Exibição de Tarefas na janela **Pilhas Paralelas**, comparado com a janela **Threads**.  
  
#### Para retomar a execução até o quarto ponto de interrupção  
  
1.  Para retomar a execução até atingir o terceiro ponto de interrupção, no menu **Depurar**, clique em **Continuar**.  Clique no cabeçalho de coluna **ID** para classificar por ID.  Você verá a ilustração a seguir.  
  
     ![Janela pilhas paralelas com tarefas em 4 Estados](~/debugger/media/pdb_walkthrough_10.png "PDB\_Walkthrough\_10")  
  
     Como a tarefa 5 foi concluída, ele não é mais exibida.  Se esse não for o caso no seu computador e o deadlock não for mostrado, volte uma etapa pressionando F11.  
  
     As tarefas 3 e 4 estão aguardando uma pela outra e estão bloqueadas.  Também há 5 novas tarefas que são filhos da tarefa 2 e estão agendadas agora.  As tarefas agendadas são aquelas iniciadas no código mas que ainda não foram executadas.  Consequentemente, suas colunas **Local** e **Atribuição de Thread** estão vazias.  
  
     Exiba a janela **Pilhas Paralelas** novamente.  O cabeçalho de cada caixa tem uma dica de ferramenta que mostra as IDs e os nomes de thread.  Alterne para o Modo de Exibição de Tarefas na janela **Pilhas Paralelas**.  Passe o mouse sobre um cabeçalho para ver o nome, a ID e o status da tarefa, como mostra a ilustração a seguir.  
  
     ![Janela pilhas paralelas com dica de ferramenta do cabeçalho](~/debugger/media/pdb_walkthrough_11.png "PDB\_Walkthrough\_11")  
  
     Você pode agrupar as tarefas por coluna.  Na janela **Tarefas Paralelas**, clique com o botão direito do mouse no cabeçalho da coluna **Status** e clique em **Agrupar por Status**.  A ilustração a seguir mostra a janela **Tarefas Paralelas** agrupada por status.  
  
     ![Janela tarefas paralelas com tarefas agrupadas](~/debugger/media/pdb_walkthrough_12.png "PDB\_Walkthrough\_12")  
  
     Também é possível agrupar por qualquer outra coluna.  Agrupando tarefas, você pode se concentrar em um subconjunto de tarefas.  Cada grupo recolhível tem uma contagem de itens que são agrupados.  Você também pode sinalizar rapidamente todos os itens no grupo clicando no botão **Sinalizar** à direita do botão **Recolher**.  
  
     ![Janela tarefas paralelas agrupada](~/debugger/media/pdb_walkthrough_12a.png "PDB\_Walkthrough\_12A")  
  
     O último recurso da janela **Tarefas Paralelas** que deve ser examinado é o menu de atalho exibido quando você clica com o botão direito do mouse em uma tarefa.  
  
     ![Contextmenu de janela tarefas paralela expandido](~/debugger/media/pdb_walkthrough_12b.png "PDB\_Walkthrough\_12B")  
  
     O menu de atalho exibe comandos diferentes, dependendo do status da tarefa.  Os comandos podem incluir **Copiar**, **Selecionar Tudo**, **Exibição Hexadecimal**, **Alternar para Tarefas**, **Congelar Thread Atribuído**, **Congelar Todos os Threads Exceto Este**, **Descongelar Thread Atribuído** e **Sinalizar**.  
  
     Você pode congelar o thread subjacente de uma tarefa, ou tarefas, ou pode congelar todos os threads exceto o atribuído.  Um thread congelado é representado na janela **Tarefas Paralelas** como estiver na janela **Threads**, por um ícone azul de *pausa*.  
  
## Resumo  
 Este passo a passo demonstrou as janelas do depurador **Tarefas Paralelas** e **Pilhas Paralelas**.  Use essas janelas em projetos reais que utilizam código multi\-threaded.  Você pode examinar o código paralelo escrito no C\+\+, no C\# ou no Visual Basic.  
  
## Consulte também  
 [Debugging Multithreaded Applications](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Programação paralela](../Topic/Parallel%20Programming%20in%20the%20.NET%20Framework.md)   
 [Tempo de Execução de Simultaneidade](/visual-cpp/parallel/concrt/concurrency-runtime)   
 [Usando a janela Pilhas Paralelas](../debugger/using-the-parallel-stacks-window.md)   
 [Usando a janela Tarefas](../debugger/using-the-tasks-window.md)