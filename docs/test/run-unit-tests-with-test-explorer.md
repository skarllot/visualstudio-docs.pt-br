---
title: "Executar testes de unidade com o Gerenciador de Testes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.unittesting.testexplorer.overview"
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "mlearned"
manager: "douge"
---
# Executar testes de unidade com o Gerenciador de Testes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o Gerenciador de testes para executar testes de unidade do Visual Studio ou projetos de teste de unidade de terceiros, agrupar testes em categorias, filtre a lista de teste, criar, salvar e executar as listas de reprodução de testes. Você também pode depurar testes e analisar um teste de desempenho e cobertura de código.  
  
##  <a name="BKMK_Contents"></a> Conteúdo  
 [Estruturas de teste de unidade e projetos de teste](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Executar testes no Gerenciador de testes](#BKMK_Run_tests_in_Test_Explorer)  
  
 [Exibir resultados do teste](#BKMK_View_test_results)  
  
 [Agrupar e filtrar a lista de teste](#BKMK_Group_and_filter_the_test_list)  
  
 [Criar listas de reprodução personalizadas](#BKMK_Create_custom_playlists)  
  
 [Depurar e analisar testes de unidade](#BKMK_Debug_and_analyze_unit_tests)  
  
 [Recursos externos](#BKMK_External_resources)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Estruturas de teste de unidade e projetos de teste  
 O Visual Studio inclui as estruturas de teste de unidade do Microsoft para código gerenciado e nativo. No entanto, Test Explorer também pode executar qualquer unidade do framework de teste que implementou um adaptador de Gerenciador de testes. Para obter mais informações sobre instalação de unidade de terceiros estruturas de teste, consulte [Instalar estruturas de teste de unidade de terceiros](../test/install-third-party-unit-test-frameworks.md)  
  
 O Gerenciador de Testes pode executar testes de vários projetos de teste em uma solução e de classes de teste que fazem parte dos projetos de código de produção. Projetos de teste podem usar estruturas de teste de unidade diferente. Quando o código em teste é escrito para o .NET Framework, o projeto de teste pode ser escrito em qualquer linguagem que também tem como alvo o .NET Framework, independentemente do idioma do código de destino. Projetos de código C\/C\+\+ nativos devem ser testados usando uma estrutura de teste de unidade do C\+\+.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Run_tests_in_Test_Explorer"></a> Executar testes no Gerenciador de testes  
 [Executar testes](#BKMK_Run_tests) **&#124;** [Executar testes após cada compilação](#BKMK_Run_tests_after_every_build)  
  
 Quando você compila o projeto de teste, os testes são exibidos no Gerenciador de testes. Se o Gerenciador de testes não estiver visível, escolha **teste** no menu do Visual Studio, escolha **Windows**, e, em seguida, escolha **Test Explorer**.  
  
 ![Explorer de teste de unidade](../ide/media/ute_failedpassednotrunsummary.png "UTE\_FailedPassedNotRunSummary")  
  
 Como executar, gravar e executar novamente os testes, o Gerenciador de testes exibe os resultados em grupos padrão de **testes com falha**, **testes aprovados**, **testes ignorada** e **Not Run Tests**. Você pode alterar a forma como o Gerenciador de testes agrupa seus testes.  
  
 Você pode executar a maioria do trabalho de encontrar, organizar e executar testes na barra de ferramentas do Gerenciador de testes.  
  
 ![Executar testes da barra de ferramentas Test Explorer](../test/media/ute_toolbar.png "UTE\_ToolBar")  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests"></a> Executar testes  
 Você pode executar todos os testes na solução, todos os testes em um grupo ou um conjunto de testes que você selecionar. Siga um destes procedimentos:  
  
-   Para executar todos os testes em uma solução, escolha **Executar todos**.  
  
-   Para executar todos os testes em um grupo padrão, escolha **Executar...** e, em seguida, escolha o grupo no menu.  
  
-   Selecione os testes individuais que você deseja executar, abra o menu de contexto de um teste selecionado e, em seguida, escolha **executar testes selecionados**.  
  
-   Se os testes individuais não têm dependências que impedem que está sendo executado em qualquer ordem, ative a execução de teste em paralelo com o ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE\_parallelicon\-small") botão de alternância na barra de ferramentas. Isso pode reduzir consideravelmente o tempo necessário para executar todos os testes.  
  
 Barra de aprovação ou reprovação na parte superior da janela do Gerenciador de testes é animada como os testes executados. Na conclusão da execução do teste, a barra de aprovação ou reprovação ficará verde se todos os testes aprovados ou ficam vermelhos se qualquer teste falhar.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests_after_every_build"></a> Executar testes após cada compilação  
  
> [!WARNING]
>  Executando testes de unidade após cada compilação é suportada no Visual Studio Enterprise.  
  
|||  
|-|-|  
|![Run after build](../test/media/ute_runafterbuild_btn.png "UTE\_RunAfterBuild\_btn")|Para executar os testes de unidade após cada compilação local, escolha **teste** no menu padrão e, em seguida, escolha **executar testes após compilação** na barra de ferramentas do Gerenciador de testes.|  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_View_test_results"></a> Exibir resultados do teste  
 [Exibir detalhes do teste](#BKMK_View_test_details) **&#124;** [Exibir o código-fonte de um método de teste](#BKMK_View_the_source_code_of_a_test_method)  
  
 Como executar, gravar e executar novamente os testes, o Gerenciador de testes exibe os resultados em grupos de **testes com falha**, **testes aprovados**, **testes ignorada** e **Not Run Tests**. O painel de detalhes na parte inferior do Gerenciador de testes exibe um resumo do teste executado.  
  
###  <a name="BKMK_View_test_details"></a> Exibir detalhes do teste  
 Para exibir os detalhes de um teste individual, selecione o teste.  
  
 ![Test execution details](../test/media/ute_testdetails.png "UTE\_TestDetails")  
  
 O painel de detalhes de teste exibe as seguintes informações:  
  
-   O nome do arquivo de origem e o número de linha do método de teste.  
  
-   O status do teste.  
  
-   O tempo decorrido que o método de teste levou para ser executado.  
  
 Se o teste falhar, o painel de detalhes também exibe:  
  
-   A mensagem retornada pela estrutura de teste de unidade para o teste.  
  
-   O rastreamento de pilha no momento em que o teste falhou.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_View_the_source_code_of_a_test_method"></a> Exibir o código\-fonte de um método de teste  
 Para exibir o código\-fonte para um método de teste no editor do Visual Studio, selecione o teste e, em seguida, escolha **Abrir teste** no menu de contexto \(teclado: F12\).  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Group_and_filter_the_test_list"></a> Agrupar e filtrar a lista de teste  
 [Agrupar a lista de teste](#BKMK_Grouping_the_test_list) **&#124;** [Agrupar por características](#BKMK_Group_by_traits) **&#124;** [Pesquisar e filtrar a lista de teste](#BKMK_Search_and_filter_the_test_list)  
  
 Gerenciador de testes permite agrupar os testes em categorias predefinidas. A maioria das estruturas de teste de unidade executados no Gerenciador de testes permitem que você defina suas próprias categorias e pares de valor\/categoria para agrupar os testes. Você também pode filtrar a lista de testes por correspondência de cadeias de caracteres em relação a propriedades de teste.  
  
###  <a name="BKMK_Grouping_the_test_list"></a> Agrupar a lista de teste  
 Para alterar a maneira que testes são organizados, escolha a seta para baixo ao lado de **Group By** botão ![Botão de teste do grupo Explorer](../test/media/ute_groupby_btn.png "UTE\_GroupBy\_btn") e selecione um novo agrupamento critérios.  
  
 ![Group tests by category in Test Explorer](../test/media/ute_groupbycategory.png "UTE\_GroupByCategory")  
  
### Grupos de Gerenciador de teste  
  
|Group|Descrição|  
|-----------|---------------|  
|**Duração**|Grupos de teste pelo tempo de execução: **rápido**, **Médio**, e **lenta**.|  
|**Resultado**|Grupos de testes, resultados da execução: **testes com falha**, **testes ignorada**, **testes aprovados**.|  
|**Características**|Grupos de teste por pares de categoria\/valor que você definir. A sintaxe para especificar valores e categorias de característica é definida pela estrutura de teste de unidade.|  
|**Projeto**|Grupos de teste, o nome dos projetos.|  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Group_by_traits"></a> Agrupar por características  
 Uma característica é geralmente um par de nome\/valor de categoria, mas também pode ser uma única categoria. Características podem ser atribuídas aos métodos que são identificados como um método de teste pela estrutura de teste de unidade. Uma estrutura de teste de unidade pode definir categorias de característica. Você pode adicionar valores para as categorias de característica para definir seus próprios pares de nome\/valor de categoria. A sintaxe para especificar valores e categorias de característica é definida pela estrutura de teste de unidade.  
  
 **Características na unidade de Microsoft Framework de teste para código gerenciado**  
  
 No Microsoft unit test framework para aplicativos gerenciados, você definir uma característica de nome \/ valor par em um  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> atributo. A estrutura de teste também contém essas características predefinidas:  
  
|Característica|Descrição|  
|--------------------|---------------|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|A categoria do proprietário é definida pela estrutura de teste de unidade e exige que você forneça um valor de cadeia de caracteres do proprietário.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|A categoria de prioridade é definida pela estrutura de teste de unidade e exige que você forneça um valor inteiro da prioridade.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|O atributo TestCategory permite que você forneça uma categoria sem um valor. Uma categoria definida pelo atributo TestCategory também pode ser a categoria de um atributo TestProperty.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|O atributo TestProperty permite que você defina o par de categoria\/valor da característica.|  
  
 **Características na unidade de Microsoft Framework de teste para C\+\+**  
  
 Para definir uma característica, use o `TEST_METHOD_ATTRIBUTE` macro. Por exemplo, para definir uma característica chamado `TEST_MY_TRAIT`:  
  
```cpp  
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)  
```  
  
 Para usar a característica definida em seus testes de unidade:  
  
```  
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
    TEST_OWNER(L"OwnerName")  
    TEST_PRIORITY(1)  
    TEST_MY_TRAIT(L"thisTraitValue")  
END_TEST_METHOD_ATTRIBUTE()  
  
TEST_METHOD(Method1)  
{     
    Logger::WriteMessage("In Method1");  
    Assert::AreEqual(0, 0);  
}  
```  
  
### Macros de atributo de característica do C\+\+  
  
|Macro|Descrição|  
|-----------|---------------|  
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Use a macro TEST\_METHOD\_ATTRIBUTE para definir uma característica.|  
|`TEST_OWNER(ownerAlias)`|Use a característica de proprietário predefinida para especificar um proprietário do método de teste.|  
|`TEST_PRIORITY(priority)`|Use a característica de prioridade predefinida para atribuir prioridades relativas a seus métodos de teste.|  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Search_and_filter_the_test_list"></a> Pesquisar e filtrar a lista de teste  
 Você pode usar o Gerenciador de testes filtros para limitar os métodos de teste em seus projetos que você exibe e executar.  
  
 Quando você digitar em uma cadeia de caracteres na caixa de pesquisa do Gerenciador de testes e a tecla ENTER, a lista de teste é filtrada para exibir somente os testes cujos nomes totalmente qualificados contêm a cadeia de caracteres.  
  
 Para filtrar por um critério diferente:  
  
1.  Abra a lista suspensa à direita da caixa de pesquisa.  
  
2.  Escolha um novo critério.  
  
3.  Insira o valor do filtro entre aspas.  
  
 ![Filter tests in Test Explorer](../test/media/ute_filtertestlist.png "UTE\_FilterTestList")  
  
> [!NOTE]
>  As pesquisas diferenciam maiúsculas de minúsculas e correspondem a cadeia especificada para qualquer parte do valor de critérios.  
  
|Qualificador|Descrição|  
|------------------|---------------|  
|**Característica**|Procura correspondências característica categoria e valor. A sintaxe para especificar as categorias de característica e valores são definidos pela estrutura de teste de unidade.|  
|**Projeto**|Procura os nomes de projeto de teste para correspondências.|  
|**Mensagem de erro**|As mensagens de erro definidas pelo usuário retornado pela falha de pesquisas afirma correspondências.|  
|**Caminho de arquivo**|Procura o nome de arquivo totalmente qualificado dos arquivos de origem do teste de correspondências.|  
|**Nome totalmente qualificado**|Procura o nome de arquivo totalmente qualificado do teste namespaces, classes e métodos de correspondências.|  
|**Saída**|Procura as mensagens de erro definidas pelo usuário que são gravadas para a saída padrão \(stdout\) ou erro padrão \(stderr\). A sintaxe para especificar as mensagens de saída são definidos pela estrutura de teste de unidade.|  
|**Resultado**|Procura os nomes de categoria de Gerenciador de testes para correspondências: **testes com falha**, **testes ignorada**, **testes aprovados**.|  
  
 Para excluir um subconjunto dos resultados de um filtro, use a seguinte sintaxe:  
  
```  
FilterName:"Criteria" -FilterName:"SubsetCriteria"  
```  
  
 Por exemplo,  
  
```  
FullName:"MyClass" - FullName:"PerfTest"  
```  
  
 Retorna todos os testes que incluem "MyClass" em seu nome, exceto os testes que também incluem "PerfTest" em seu nome.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Create_custom_playlists"></a> Criar listas de reprodução personalizadas  
 Você pode criar e salvar uma lista de testes que você deseja executar ou exibir como um grupo. Quando você seleciona uma lista de reprodução, são exibidos os testes na lista Gerenciador de testes. Você pode adicionar um teste a mais de uma lista de reprodução, e todos os testes em seu projeto estão disponíveis quando você escolher o padrão **todos os testes** lista de reprodução.  
  
 ![Choose a playlist](../test/media/ute_playlist.png "UTE\_Playlist")  
  
 **Para criar uma lista de reprodução**, escolha um ou mais testes no Gerenciador de testes. No menu de contexto, escolha **Adicionar à lista de reprodução**, **NewPlaylist**. Salve o arquivo com o nome e local que você especificar na **Criar nova lista de reprodução** caixa de diálogo.  
  
 **Para adicionar testes a uma lista de reprodução**, escolha um ou mais testes no Gerenciador de testes. No menu de contexto, escolha **Adicionar à lista de reprodução**, e, em seguida, escolha a lista de reprodução que você deseja adicionar os testes.  
  
 **Para abrir uma lista de reprodução**, escolha o teste, a lista de reprodução no menu do Visual Studio, e escolha na lista de listas de reprodução usadas recentemente, ou escolha Abrir a lista de reprodução para especificar o nome e o local da lista de reprodução.  
  
 Se os testes individuais não têm dependências que impedem que está sendo executado em qualquer ordem, ative a execução de teste em paralelo com o ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE\_parallelicon\-small") botão de alternância na barra de ferramentas. Isso pode reduzir consideravelmente o tempo necessário para executar todos os testes.  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_Debug_and_analyze_unit_tests"></a> Depurar e analisar testes de unidade  
 [Depurar testes de unidade](#BKMK_Debug_unit_tests) **&#124;** [Diagnosticar problemas de desempenho do método de teste](#BKMK_Diagnose_test_method_performance_issues) **&#124;** [Analisar a cobertura de código de teste de unidade](#BKMK_Analyzeunit_test_code_coverage)  
  
###  <a name="BKMK_Debug_unit_tests"></a> Depurar testes de unidade  
 Você pode usar o Gerenciador de testes para iniciar uma sessão de depuração para os testes. Passar pelo código com o depurador do Visual Studio permite\-lhe navegar facilmente entre os testes de unidade e o projeto sendo testado. Para iniciar a depuração:  
  
1.  No editor do Visual Studio, defina um ponto de interrupção em um ou mais métodos de teste que deseje depurar.  
  
    > [!NOTE]
    >  Como os métodos de teste podem ser executados em qualquer ordem, defina pontos de interrupção em todos os métodos de teste que deseje depurar.  
  
2.  No Gerenciador de testes, selecione os métodos de teste e escolha **Depurar testes selecionados** no menu de contexto.  
  
 Para obter mais informações sobre o depurador, consulte [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
###  <a name="BKMK_Diagnose_test_method_performance_issues"></a> Diagnosticar problemas de desempenho do método de teste  
 Para diagnosticar por que um método de teste está levando muito tempo, selecione o método no Gerenciador de testes e, em seguida, escolha o perfil no menu de contexto. Consulte [Performance Explorer](../profiling/performance-explorer.md).  
  
###  <a name="BKMK_Analyzeunit_test_code_coverage"></a> Analisar a cobertura de código de teste de unidade  
  
> [!NOTE]
>  Cobertura de código de teste de unidade está disponível apenas no Visual Studio Enterprise.  
  
 Você pode determinar a quantidade de seu código de produto que realmente está sendo testado por seus testes de unidade usando a ferramenta de cobertura de código do Visual Studio. Você pode executar a cobertura de código em testes selecionados ou em todos os testes em uma solução.  
  
 Para executar a cobertura de código para métodos de teste em uma solução:  
  
1.  Escolha **testes** no menu do Visual Studio e, em seguida, escolha **Analisar cobertura de código**.  
  
2.  Escolha um dos seguintes comandos do submenu:  
  
    -   **Testes selecionados** executa os métodos de teste que você selecionou no Gerenciador de testes.  
  
    -   **Todos os testes** executa todos os métodos de teste na solução.  
  
 A janela Code Coverage Results exibe a porcentagem dos blocos que foram exercidos por linha, função, classe, namespace e módulo de código do produto.  
  
 Para obter mais informações, consulte [Usando cobertura de código para determinar quanto código está sendo testado](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 ![Back to top](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Conteúdo](#BKMK_Contents)  
  
##  <a name="BKMK_External_resources"></a> Recursos externos  
  
###  <a name="BKMK_Guidance"></a> Diretrizes  
 [Teste para entrega contínua com Visual Studio 2012 – capítulo 2: teste de unidade: Testando o interior](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## Consulte também  
 [Teste de unidade de código](../test/unit-test-your-code.md)   
 [Executar um teste de unidade como um processo de 64 bits](../test/run-a-unit-test-as-a-64-bit-process.md)