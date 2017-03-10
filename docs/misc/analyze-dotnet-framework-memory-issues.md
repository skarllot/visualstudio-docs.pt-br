---
title: "Analisar problemas de mem&#243;ria .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.diagnostics.managedmemoryanalysis"
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "susanno"
manager: "douge"
---
# Analisar problemas de mem&#243;ria .NET Framework
Encontre perdas de memória e uso ineficiente da memória no código do .NET Framework com o analisador de memória gerenciada do Visual Studio.  A versão mínima do .NET Framework do código de destino é o .NET Framework 4.5.  
  
 A ferramenta de análise da memória analisa informações em *arquivos de despejo com dados do heap*, onde fica uma cópia dos objetos na memória de um aplicativo.  Você pode coletar arquivos de despejo \(.dmp\) do IDE do Visual Studio ou usar outras ferramentas de sistema.  
  
-   É possível analisar um único instantâneo para compreender o impacto relativo dos tipos de objeto sobre o uso da memória e encontrar o código no aplicativo que usa a memória de maneira ineficiente.  
  
-   Também é possível comparar \(*diff*\) dois instantâneos de um aplicativo para encontrar áreas no código que causam o aumento do uso da memória com o passar do tempo.  
  
 Para ver um passo a passo do analisador de memória gerenciada, consulte [Usando o Visual Studio 2013 para diagnosticar problemas de memória do .NET na produção](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) no blog Visual Studio ALM \+ Team Foundation Server.  
  
##  <a name="BKMK_Contents"></a> Conteúdo  
 [Uso da memória em aplicativos do .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identificar um problema de memória em um aplicativo](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Coletar instantâneos da memória](#BKMK_Collect_memory_snapshots)  
  
 [Analisar o uso da memória](#BKMK_Analyze_memory_use)  
  
##  <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Uso da memória em aplicativos do .NET Framework  
 Como o .NET Framework é um tempo de execução com coleta de lixo, na maioria dos aplicativos, o uso da memória não é um problema.  Mas em aplicativos de longa execução, como serviços e aplicativos Web, e em dispositivos que tenham uma quantidade de memória limitada, o acúmulo de objetos na memória pode afetar o desempenho do aplicativo e o dispositivo no qual é executado.  O uso excessivo da memória poderá desabastecer o aplicativo e o computador de recursos se o coletor de lixo estiver sempre em execução ou se o sistema operacional for forçado a transferir memória entre RAM e disco.  No pior dos casos, um aplicativo pode falhar com uma exceção "Falta de memória".  
  
 O *heap gerenciado* do .NET é uma região da memória virtual onde são armazenados os objetos de referência criados por um aplicativo.  O tempo de vida dos objetos é gerenciada pelo GC \(coletor de lixo\).  O coletor de lixo usa referências para acompanhar objetos que ocupam blocos de memória.  Uma referência é criada quando um objeto é criado e atribuído a uma variável.  Um único objeto pode ter várias referências.  Por exemplo, as referências adicionais a um objeto podem ser criadas adicionando\-se o objeto a uma classe, coleção ou outra estrutura de dados, ou atribuindo o objeto a uma segunda variável.  Uma maneira menos óbvia de criar uma referência é com um objeto adicionando um manipulador ao evento de outro objeto.  Nesse caso, o segundo objeto mantém a referência ao primeiro objeto até o manipulador ser removido explicitamente ou o segundo objeto ser destruído.  
  
 Para cada aplicativo, o GC mantém uma árvore de referências que acompanha os objetos mencionados pelo aplicativo.  A *árvore de referência* tem um conjunto de raízes, que inclui objetos globais e estáticos, além de pilhas de threads e objetos instanciados dinamicamente.  Um objeto será raiz se tiver pelo menos um objeto pai mantendo uma referência a ele.  O GC só poderá recuperar a memória de um objeto quando nenhum outro objeto ou variável no aplicativo tiver uma referência a ele.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identificar um problema de memória em um aplicativo  
 O sintoma mais visível de problemas de memória é o desempenho do aplicativo, especialmente se o desempenho cair com o passar do tempo.  A queda no desempenho de outros aplicativos enquanto o aplicativo está em execução também pode indicar uma perda de memória.  Se você suspeitar de um problema de memória, use uma ferramenta como o Gerenciador de tarefas ou[Windows Performance Monitor](http://technet.microsoft.com/library/cc749249.aspx)para investigar mais.  Por obter exemplo, procure um aumento no tamanho total da memória que não seja possível explicar como uma origem possível de perdas de memória:  
  
 ![Consistent memory growth in Resource Monitor](../misc/media/mngdmem_resourcemanagerconsistentgrowth.png "MNGDMEM\_ResourceManagerConsistentGrowth")  
  
 Você também pode notar picos de memória maiores que o seu conhecimento do código sugeriria, o que pode indicar uso ineficiente da memória em um procedimento:  
  
 ![Memory spikes in Resource Manager](../Image/MNGDMEM_ResourceManagerSpikes.png "MNGDMEM\_ResourceManagerSpikes")  
  
##  <a name="BKMK_Collect_memory_snapshots"></a> Coletar instantâneos da memória  
 A ferramenta de análise da memória analisa informações em *arquivos de despejo* que contêm informações do heap.  Você pode criar arquivos de despejo no Visual Studio, ou você pode usar uma ferramenta como[ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx)de[Windows Sysinternals](http://technet.microsoft.com/sysinternals).  Consulte [O que é um despejo e como faço para criar um?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) no blog da equipe do Depurador do Visual Studio.  
  
> [!NOTE]
>  A maioria das ferramentas pode coletar informações de despejo com ou sem dados completos de memória do heap.  O analisador de memória do Visual Studio requer informações completas do heap.  
  
 **Para coletar um despejo do Visual Studio**  
  
1.  É possível criar um arquivo de despejo para um processo iniciado em um projeto do Visual Studio ou anexar o depurador a um processo em execução.  Consulte[Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2.  Pare a execução.  O depurador para em uma exceção ou em um ponto de interrupção quando você escolhe **Interromper Tudo**, no menu **Depurar**  
  
3.  No menu **Depurar**, escolha **Salvar Despejo Como**.  Na caixa de diálogo **Salvar Despejo Como**, especifique um local e verifique se **Minidespejo com Heap** \(o padrão\) está selecionado na lista **Salvar como tipo**.  
  
 **Para comparar dois instantâneos de memória**  
  
 Para analisar o aumento do uso da memória de um aplicativo, colete dois arquivos de despejo de uma única instância do aplicativo.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Analyze_memory_use"></a> Analisar o uso da memória  
 [Filtrar a lista de objetos](#BKMK_Filter_the_list_of_objects) **&#124;** [Analisar dados da memória de um único instantâneo](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [Comparar dois instantâneos de memória](#BKMK_Compare_two_memory_snapshots)  
  
 Para analisar um arquivo de despejo em busca de problemas de uso da memória:  
  
1.  No Visual Studio, escolha **Arquivo**, **Abrir** e especifique o arquivo de despejo.  
  
2.  Na página **Resumo de Arquivo de Minidump**, escolha **Depurar Memória Gerenciada**.  
  
     ![Dump file summary page](../misc/media/mngdmem_dumpfilesummary.png "MNGDMEM\_DumpFileSummary")  
  
 O analisador de memória começa uma sessão de depuração para analisar o arquivo e exibe os resultados na página Exibição do Heap:  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Filter_the_list_of_objects"></a> Filtrar a lista de objetos  
 Por padrão, o analisador de memória filtra a lista de objetos em um instantâneo de memória para mostrar apenas os tipos e as instâncias codificados pelo usuário e somente aqueles tipos cujo tamanho total inclusivo excede uma porcentagem limite do tamanho total do heap.  É possível alterar estas opções na lista **Configurações de Exibição**:  
  
|||  
|-|-|  
|**Habilitar Apenas Meu Código**|Habilitar Apenas Meu Código oculta os objetos de sistema mais comuns, para que apenas os tipos criados por você sejam exibidos na lista.<br /><br /> Também é possível definir a opção Habilitar Apenas Meu Código na caixa de diálogo **Opções** do Visual Studio.  No menu de **Depurar**, escolha **Opções e Configurações**.  Na guia **Depuração**\/**Geral**, marque ou desmarque **Habilitar Apenas Meu Código**.|  
|**Recolher Objetos Pequenos**|**Recolher pequenos objetos**oculta todos os tipos cujo tamanho inclusivo total seja menor que 0,5% do tamanho total do heap.|  
  
 Também é possível filtrar a lista de tipos inserindo uma cadeia de caracteres na caixa **Pesquisar**.  A lista exibe apenas os tipos cujos nomes contenham a cadeia de caracteres.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analisar dados da memória de um único instantâneo  
 O Visual Studio inicia uma nova sessão de depuração para analisar o arquivo e exibe os dados da memória na janela Exibição do Heap.  
  
 ![The Object Type list](../misc/media/dbg_mma_objecttypelist.png "DBG\_MMA\_ObjectTypeList")  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
#### Tabela Tipo de Objeto  
 A tabela superior lista os tipos de objetos mantidos na memória.  
  
-   **Contagem**mostra o número de instâncias do tipo no instantâneo.  
  
-   **Tamanho \(Bytes\)**é o tamanho de todas as instâncias do tipo, excluindo o tamanho dos objetos que ele contém referências a.  O  
  
-   **Tamanho inclusivo \(Bytes\)**inclui os tamanhos de objetos referenciados.  
  
 Você pode escolher o ícone de instâncias \(![The instance icon in the Object Type column](../misc/media/dbg_mma_instancesicon.png "DBG\_MMA\_InstancesIcon")\) no**tipo de objeto**coluna para exibir uma lista de instâncias do tipo.  
  
#### Tabela Instância  
 ![Instances table](../misc/media/dbg_mma_instancestable.png "DBG\_MMA\_InstancesTable")  
  
-   **Instância**é o local de memória do objeto que serve como o identificador de objeto do objeto  
  
-   **Valor**mostra o valor real de tipos de valor.  É possível focalizar o nome de um tipo de referência para exibir os valores de dados em uma dica de dados.  
  
     ![Instance values in a data tip](../Image/DBG_MMA_InstanceValuesInDataTip.png "DBG\_MMA\_InstanceValuesInDataTip")  
  
-   **Tamanho \(Bytes\)**é o tamanho do objeto, excluindo o tamanho dos objetos que ele contém referências a.  O  
  
-   **Tamanho inclusivo \(Bytes\)**inclui os tamanhos de objetos referenciados.  
  
 Por padrão, os tipos e as instâncias são classificados por **Tamanho Inclusivo \(Bytes\)**.  Escolha um cabeçalho de coluna na lista para alterar a ordem de classificação.  
  
#### Caminhos para a Raiz  
  
-   No caso de um tipo selecionado na tabela **Tipo de Objeto**, a tabela **Caminhos para a Raiz** mostra as hierarquias de tipo exclusivo que levam até objetos raiz de todos os objetos do tipo, além do número de referências ao tipo acima dele na hierarquia.  
  
-   No caso de um objeto selecionado na instância de um tipo, **Caminhos para a Raiz** mostra um gráfico dos objetos reais que mantém uma referência à instância.  É possível focalizar o nome do objeto para exibir os valores de dados em uma dica de dados.  
  
#### Tipos Referenciados\/Objetos Referenciados  
  
-   No caso de um tipo selecionado na tabela **Tipo de Objeto**, a guia **Tipos Referenciados** mostra o tamanho e o número de tipos referenciados mantidos por todos os objetos do tipo selecionado.  
  
-   No caso de uma instância selecionada de um tipo, **Objetos Referenciados** mostra os objetos mantidos pela instância selecionada.  É possível focalizar o nome para exibir os valores de dados em uma dica de dados.  
  
 **Referências circulares**  
  
 Um objeto pode referenciar um segundo objeto que mantém direta ou indiretamente uma referência ao primeiro objeto.  Ao encontrar essa situação, o analisador de memória para de expandir o caminho de referência e adiciona uma anotação **\[Ciclo Detectado\]** à listagem do primeiro objeto e para.  
  
 **Tipos de raiz**  
  
 O analisador de memória adiciona anotações a objetos raiz que descrevam o tipo de referência mantido:  
  
|Anotação|Descrição|  
|--------------|---------------|  
|**Variável estática** `VariableName`|Uma variável estática.  `VariableName`é o nome da variável.|  
|**Alça de Finalização**|Uma referência da fila do finalizador|  
|**Variável Local**|Uma variável local.|  
|**Alça Forte**|Uma alça para uma referência forte da tabela de identificador de objeto.|  
|**Alça  Alça Fixa**|Um objeto fixo assíncrono da tabela de identificador de objeto.|  
|**Alça Dependente**|Um objeto dependente da tabela de identificador de objeto.|  
|**Alça Fixa**|Uma referência forte fixa da tabela de identificador de objeto.|  
|**Alça RefCount**|Um objeto com contagem de referência da tabela de identificador de objeto.|  
|**Alça SizedRef**|Uma alça forte que mantém um tamanho aproximado do fechamento coletivo de todos os objetos e raízes de objeto no momento da coleta de lixo.|  
|**Variável local fixa**|Uma variável local fixa.|  
  
###  <a name="BKMK_Compare_two_memory_snapshots"></a> Comparar dois instantâneos de memória  
 É possível comparar dois arquivos de despejo de um processo para encontrar objetos que possam ser a causa de perdas de memória.  O intervalo entre a coleta do primeiro arquivo \(anterior\) e do segundo arquivo \(posterior\) deve ser grande o suficiente para que o aumento no número de objetos perdidos fique claramente aparente.  Para comparar os dois arquivos:  
  
1.  Abra o segundo arquivo de despejo e escolha **Depurar Memória Gerenciada** na página **Resumo de Arquivo de Minidump**.  
  
2.  Na página de relatório de análise da memória, abra a lista **Selecionar linha de base** e escolha **Procurar** para especificar o primeiro arquivo de despejo.  
  
 O analisador adiciona colunas ao painel superior do relatório que exibe a diferença entre **Contagem**, **Tamanho** e **Tamanho Inclusivo** dos tipos para esses valores no instantâneo anterior.  
  
 ![Diff columns in the type list](../misc/media/mngdmem_diffcolumns.png "MNGDMEM\_DiffColumns")  
  
 Uma coluna **Diferença de Contagem de Referência** também é adicionada à tabela **Caminhos para a Raiz**.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
## Consulte também  
 [Blog VS ALM TFS: usando o Visual Studio 2013 para diagnosticar problemas de memória do .NET na produção](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [canal 9 &#124; O Visual Studio TV &#124; Gerenciado análise de memória](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [canal 9 &#124; Ferramentas do Visual Studio &#124; Gerenciado análise de memória no Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)