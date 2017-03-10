---
title: "Especificar arquivos de s&#237;mbolo (.pdb) e de origem no Depurador do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Debugger.Native"
  - "VS.ToolsOptionsPages.Debugger.Symbols"
  - "vs.debug.options.Native"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "código-fonte"
  - "arquivos .dbg"
  - "código-fonte, gerenciamento"
  - "símbolos, gerenciando"
  - "arquivos .pdb"
  - "arquivos dbg"
  - "arquivos pdb"
  - "depurador"
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Especificar arquivos de s&#237;mbolo (.pdb) e de origem no Depurador do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um arquivo de banco de dados \(. PDB\) do programa, também chamado de arquivo de símbolo, mapeia os identificadores que você cria em arquivos de origem para classes, métodos e outros códigos para os identificadores que são usadas em executáveis compilados do seu projeto. O arquivo. PDB também mapeia as instruções no código\-fonte para instruções de execução nos arquivos executáveis. O depurador usa essas informações para determinar duas informações cruciais: o número de arquivo e a linha de origem que são exibidos no IDE do Visual Studio e o local no executável parar quando você definir um ponto de interrupção. Um arquivo de símbolo também contém o local original dos arquivos de origem e, opcionalmente, o local de onde os arquivos de origem podem ser recuperados de um servidor de origem.  
  
 Quando você depurar um projeto no IDE do Visual Studio, o depurador saberá que o local padrão para os arquivos. PDB e código\-fonte para seu código. Se você quiser depurar o código fora de seu código de origem do projeto, como o Windows ou o código de terceiros suas chamadas de projeto, você precisa especificar o local do. PDB \(e, opcionalmente, os arquivos de origem do código externo\) e esses arquivos precisam corresponder exatamente à compilação dos executáveis.  
  
 Antes do Visual Studio 2012, quando você depurar código gerenciado em um dispositivo remoto necessária colocar os arquivos de símbolo no computador remoto. Esse não é mais o caso. Todos os arquivos de símbolo devem estar localizados no computador local ou em um local especificado no **Ferramentas \/ opções \/ depuração \/ símbolos** página.  
  
##  <a name="BKMK_Find_symbol___pdb__files"></a> Onde o depurador procura por arquivos. PDB  
  
1.  O local especificado dentro da DLL ou o arquivo executável.  
  
     \(Por padrão, se você compilou uma DLL ou um arquivo executável no seu computador, o vinculador coloca o nome de arquivo e caminho completo do arquivo. PDB associado dentro da DLL ou o arquivo executável. O depurador verifica primeiro se o arquivo de símbolo existe no local especificado dentro da DLL ou o arquivo executável. Isso é útil, porque você sempre tenha símbolos disponíveis para o código que compilou no seu computador.\)  
  
2.  arquivos. PDB que podem estar presentes na mesma pasta que o arquivo executável ou DLL.  
  
3.  Qualquer pasta de cache de símbolo local.  
  
4.  Qualquer rede, internet ou servidores de símbolo local e locais que são especificados, como o Microsoft symbol server se habilitado.  
  
###  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Por que arquivos de símbolo precisam coincidir exatamente com os arquivos executáveis?  
 O depurador carregará apenas um arquivo. PDB para um arquivo executável que corresponda exatamente ao arquivo. PDB criado quando o executável foi compilado \(isto é, o. PDB deve ser o original ou uma cópia do arquivo. PDB original\). Como o compilador é otimizado para velocidade de compilação, além de sua tarefa principal de criação de código correto e eficiente, o layout real de um executável pode alterar mesmo se o próprio código não mudou. Para obter mais informações, consulte [por que o Visual Studio exigem arquivos de símbolo do depurador para corresponder exatamente os arquivos binários que foram criados com?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).  
  
###  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Especificar o comportamento de carregamento e locais de símbolos  
 Quando você depurar um projeto no IDE do VS, o depurador carrega automaticamente os arquivos de símbolo estão localizados no diretório do projeto. Você pode especificar caminhos de pesquisa alternativos e servidores de símbolo para a Microsoft, Windows ou componentes de terceiros em **Ferramentas \/ opções \/ depuração \/ símbolos**. Você também pode especificar que você deseja que o depurador para automaticamente carregar símbolos para os módulos específicos. E você pode alterar essas configurações manualmente enquanto você está depurando ativamente.  
  
1.  No Visual Studio, abra o **Ferramentas \/ opções \/ depuração \/ símbolos** página.  
  
     ![Ferramentas &#45; página de opções &#45; depuração &#45; símbolos](../debugger/media/dbg_tools_options_symbols.png "DBG\_Tools\_Options\_Symbols")  
  
2.  Escolha a pasta ![Ferramentas &#47; opções &#47; ícone de pasta&#47;símbolos de depuração](../debugger/media/dbg_tools_options_foldersicon.png "DBG\_Tools\_Options\_FoldersIcon") ícone. Texto editável aparece no **símbolos de locais de arquivo \(. PDB\)** caixa.  
  
3.  Digite a URL ou caminho do diretório do servidor de símbolos ou local do símbolo. Conclusão de instrução ajuda a localizar o formato correto.  
  
4.  Para melhorar o símbolo de desempenho do carregamento digite o caminho de um diretório local onde os símbolos podem ser copiados por servidores de símbolo no **armazenar em Cache os símbolos neste diretório** caixa um diretório local símbolos podem ser copiados para.  
  
    > [!NOTE]
    >  Não coloque o cache de símbolo em uma pasta protegida \(como a pasta C:\\Windows ou uma de suas subpastas\). Use uma pasta de leitura \/ gravação.  
  
 **Especificar o comportamento de carregamento de símbolo**  
  
 Você pode especificar os arquivos que você deseja carregar automaticamente a partir de **de símbolos de locais de arquivo \(. PDB\)** caixa locais quando você iniciar a depuração. Arquivos de símbolo no diretório do projeto são sempre carregados.  
  
1.  Escolha **todos os módulos, a menos que excluídos** para carregar todos os símbolos de todos os módulos, exceto aqueles que você especifica quando você escolhe o **especificar módulos excluídos** link.  
  
2.  Escolha o **somente os módulos especificados** opção e, em seguida, escolha **especificar módulos** para listar os módulos que arquivos de símbolo que deseja carregar automaticamente. Os arquivos de símbolo para outros módulos são ignorados.  
  
 **Especificar opções adicionais de símbolo**  
  
 Você também pode definir as opções a seguir sobre o **Ferramentas \/ opções \/ depuração \/ símbolos** página:  
  
 **Avisar se não houver símbolos na inicialização \(somente nativo\)**  
  
 Quando selecionada, exibe uma caixa de diálogo de aviso quando você tenta depurar um programa para o qual o depurador não tem nenhuma informação simbólica.  
  
 **Carregar exportações de DLL**  
  
 Quando selecionada, carrega o DLL exportar tabelas. Informações simbólicas das tabelas de exportação DLL podem ser útil se você estiver trabalhando com mensagens do Windows, procedimentos do Windows \(WindowProcs\), objetos COM, ou marshaling ou qualquer DLL para o qual você não tem símbolos. Informações de exportação de DLL de leitura envolve alguma sobrecarga. Portanto, esse recurso está desativado por padrão.  
  
 Para ver quais símbolos estão disponíveis na tabela de exportação de uma DLL, use `dumpbin /exports`. Símbolos estão disponíveis para qualquer DLL do sistema de 32 bits. Lendo o `dumpbin /exports` de saída, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Nomes de função de tabelas de exportação DLL podem aparecer truncados em outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual \(a mais profundamente aninhada\) na parte superior. Para obter mais informações, consulte [dumpbin\/exportações](/visual-cpp/build/reference/dash-exports).  
  
###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Usar servidores de símbolo para localizar arquivos de símbolo não no computador local  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode baixar arquivos de símbolo de depuração de servidores de símbolo que implementam o protocolo symsrv.[Visual Studio Team Foundation Server](../Topic/Index%20and%20publish%20symbol%20data.md) e [as ferramentas de depuração para Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) são duas ferramentas que podem implementar servidores de símbolo. Especifique os servidores de símbolo para usar no VS **opções** caixa de diálogo.  
  
 Servidores de símbolo que você pode usar incluem:  
  
 **Servidores de símbolos públicos da Microsoft**  
  
 Para depurar uma falha que ocorre durante uma chamada para uma DLL do sistema ou em uma biblioteca de terceiros, você geralmente precisará arquivos. PDB do sistema, que contêm símbolos para DLLs do Windows, EXEs e drivers de dispositivo. Você pode obter esses símbolos de servidores de símbolo públicos da Microsoft. Servidores de símbolo públicos da Microsoft fornecem símbolos para sistemas operacionais Windows, além de MDAC, IIS, ISA e o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Para usar servidores de símbolo da Microsoft, escolha **Opções e configurações** sobre o **Depurar** menu e escolha **símbolos**. Selecione **servidores de símbolo Microsoft**.  
  
 **Servidores de símbolo em uma rede interna ou em seu computador local**  
  
 Sua equipe ou empresa pode criar servidores de símbolo para seus próprios produtos e como um cache para símbolos de fontes externas. Você pode ter um servidor de símbolo em seu próprio computador. Você pode inserir o local dos servidores de símbolo como uma URL ou um caminho **depuração**\/**símbolos** página do VS **caixa de diálogo Opções**.  
  
 **Servidores de símbolo de terceiros**  
  
 Fornecedores de aplicativos do Windows e bibliotecas podem fornecer acesso ao servidor de símbolo na internet. Você também insere a URL desses servidores de símbolo de **depuração**\/**símbolos** página,  
  
> [!NOTE]
>  Se você usar um servidor de símbolo diferente de servidores de símbolos públicos da Microsoft, certifique\-se de que o servidor de símbolos e seu caminho são confiáveis. Como arquivos de símbolo podem conter códigos executáveis arbitrários, você pode ser exposto a ameaças de segurança.  
  
###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Localizar e carregar símbolos durante a depuração  
 A qualquer momento que o depurador está no modo de interrupção, você pode carregar símbolos para um módulo que foi excluído anteriormente pelas opções de depurador ou que o compilador não foi possível localizar. Você pode carregar símbolos nos menus de atalho da pilha de chamadas, módulos, locais, Autos e todas as janelas de observação. Se o depurador interrompe no código que não tenha arquivos de símbolo ou de origem disponíveis, será exibida uma janela de documento. Aqui você pode encontrar informações sobre os arquivos ausentes e executar ações para localizar e carregá\-los.  
  
 **Localizar símbolos com as páginas de documento nenhum símbolo carregado**  
  
 Há várias formas para que o depurador entrar no código que não tem símbolos disponíveis:  
  
1.  Depuração em código.  
  
2.  Separando o código de um ponto de interrupção ou exceção.  
  
3.  Alternando para um thread diferente.  
  
4.  Alterar o quadro de pilha clicando duas vezes em um quadro na janela pilha de chamadas.  
  
 Quando um desses eventos ocorre, o depurador exibe o **Nenhum símbolo carregado** página para ajudá\-lo a localizar e carregar os símbolos necessários.  
  
 ![Nenhuma página carregada de símbolos](../debugger/media/dbg_nosymbolsloaded.png "DBG\_NoSymbolsLoaded")  
  
-   Para alterar os caminhos de pesquisa, escolha um caminho não selecionado ou escolha **novo** e digite um novo caminho. Escolha **carregar** para procurar novamente os caminhos e carregar o arquivo de símbolo se ela for encontrada.  
  
-   Escolha **Procurar e localizar***nome executável***...** para substituir quaisquer opções de símbolo e repita os caminhos de pesquisa. O arquivo de símbolo é carregado, se ele for encontrado, ou um Explorador de arquivos é exibido para que você selecione manualmente o arquivo de símbolo.  
  
-   Escolha **Alterar configurações de símbolo...** para exibir o **depuração** \/ **símbolos** página da caixa de diálogo Opções do VS.  
  
-   Escolha **Exibir desmontagem** para mostrar a desmontagem em uma nova janela uma vez.  
  
-   Para sempre mostrar a desmontagem quando os arquivos de origem ou de símbolo não forem localizados, escolha o **caixa de diálogo Opções** link e selecione **Habilitar depuração no nível do endereço** e **Mostrar desmontagem se a origem não está disponível**.  
  
     ![Opções &#47; depuração &#47; geral opções de desmontagem](../debugger/media/dbg_options_general_disassembly_checkbox.png "DBG\_Options\_General\_disassembly\_checkbox")  
  
 **Alterar opções de símbolo no menu de atalho**  
  
 Enquanto você estiver no modo de interrupção, você pode localizar e carregar símbolos para itens que são exibidos na pilha de chamadas, módulos, locais, Autos e todas as janelas de observação. Selecione um item na janela, abra o menu de atalho e escolha uma das seguintes opções:  
  
|Opção|Descrição|  
|-----------|---------------|  
|**Carregar símbolos**|Tenta carregar símbolos de locais especificados no **depuração** \/ **símbolos** página do **opções** caixa de diálogo. Se o arquivo de símbolo não for encontrado, o Explorador de arquivos é iniciado para que você possa especificar um novo local de pesquisa.|  
|**Informações de carga de símbolo**|Apresenta informações que mostram o local de um arquivo de símbolo carregado ou os locais que foram pesquisados se o depurador não pode localizar o arquivo.|  
|**Configurações de símbolo...**|Abre o **depuração** \/ **símbolos** página do VS **opções** caixa de diálogo.|  
|**Sempre carregar automaticamente**|Adiciona o arquivo de símbolo à lista de arquivos que são carregados automaticamente pelo depurador.|  
  
###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Definir opções do compilador para arquivos de símbolo  
 Quando você compilar seu projeto no IDE do VS e use o padrão de **Depurar** configuração de compilação, o C\+\+ e compiladores gerenciados criam os arquivos de símbolos apropriados para seu código. Você também pode definir opções de compilador na linha de comando para criar os arquivos de símbolo.  
  
 **Opções do C\+\+**  
  
 Um arquivo de banco de dados \(. PDB\) programa contém informações de depuração de estado que permite vinculação incremental de uma configuração de depuração do seu programa. Um arquivo. PDB é criado quando você compila com [\/ZI ou \/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) \(para C\/C\+\+\).  
  
 Em [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)], o [\/Fd](/visual-cpp/build/reference/fd-program-database-file-name) opção nomeia o arquivo. PDB criado pelo compilador. Quando você cria um projeto no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usando assistentes, a **\/Fd** opção é definida para criar um arquivo. PDB chamado *projeto*. PDB.  
  
 Se você criar seu aplicativo C\/C\+\+ usando um makefile e especificar **\/ZI** ou **\/Zi** sem **\/Fd**, você acabará com dois arquivos. PDB:  
  
-   VC*x*. PDB, onde *x* representa a versão do Visual C\+\+, por exemplo, vc11. Esse arquivo armazena todas as informações de depuração para os arquivos OBJ individuais e reside no mesmo diretório que o makefile do projeto.  
  
-   PDB esse arquivo armazena todas as informações de depuração para o arquivo the.exe. Para C\/C\+\+, ele reside na subpasta \\Debug.  
  
 Cada vez que ele cria um arquivo OBJ, o compilador C\/C\+\+ mescla informações de depuração em VC*x*. PDB. As informações inseridas incluem informações de tipo mas não incluem informações de símbolo como definições de função. Até mesmo se todos os arquivos de origem incluam arquivos de cabeçalho como \< Windows. h \>, os typedefs desses cabeçalhos são armazenados apenas uma vez, em vez de estarem em todos os arquivos OBJ.  
  
 O vinculador cria Project. PDB, que contém informações de depuração para o arquivo EXE do projeto. O arquivo Project PDB contém informações completas da depuração, incluindo protótipos de função, não apenas as informações encontradas no VC*x*. PDB. Os dois arquivos. PDB permitem atualizações incrementais. O vinculador também incorpora o caminho para o arquivo. PDB no arquivo .exe ou. dll que ele cria.  
  
 O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depurador usa o caminho para o arquivo. PDB no arquivo EXE ou DLL para localizar o arquivo Project PDB. Se o depurador não pode localizar o arquivo. PDB nesse local ou se o caminho for inválido \(por exemplo, se o projeto foi movido para outro computador\), o depurador pesquisará o caminho que contém o EXE, os caminhos de símbolo especificado no **opções** caixa de diálogo \(**depuração** pasta **símbolos** nó\). O depurador não carregará um arquivo. PDB que não coincide com o arquivo executável que está sendo depurado. Se o depurador não pode localizar um arquivo. PDB, um **Localizar símbolos** caixa de diálogo aparece, que permite que você procure por símbolos ou adicione locais ao caminho de pesquisa.  
  
 **Opções do .NET framework**  
  
 Um arquivo de banco de dados \(. PDB\) programa contém informações de depuração de estado que permite vinculação incremental de uma configuração de depuração do seu programa. Um arquivo. PDB é criado quando você compila com **\/Debug**. Você pode criar aplicativos com **\/Debug: full** ou **\/Debug: pdbonly**. Compilando com **\/Debug: full** gera código depurável. Compilando com **\/Debug: pdbonly** gera arquivos. PDB, mas não gera o `DebuggableAttribute` que informa o compilador JIT que as informações de depuração estão disponíveis. Use **\/Debug: pdbonly** se você deseja gerar arquivos. PDB para uma compilação de versão que você não deseja que seja depurável. Para obter mais informações, consulte [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) ou [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).  
  
 O [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depurador usa o caminho para o arquivo. PDB no arquivo EXE ou DLL para localizar o arquivo Project PDB. Se o depurador não pode localizar o arquivo. PDB nesse local, ou se o caminho for inválido, o depurador pesquisará o caminho que contém o EXE e, em seguida, os caminhos de símbolo especificados no **opções** caixa de diálogo. Esse caminho é geralmente a **depuração** pasta o **símbolos** nó. O depurador não carregará um arquivo. PDB que não coincide com o arquivo executável que está sendo depurado. Se o depurador não pode localizar um arquivo. PDB, um **Localizar símbolos** caixa de diálogo aparece, que permite que você procure por símbolos ou adicione locais ao caminho de pesquisa.  
  
 **Aplicativos Web**  
  
 O arquivo de configuração do aplicativo \(Web. config\) deve ser definido como modo de depuração. Depuração modo faz com que o ASP.NET gere símbolos para arquivos gerados dinamicamente e permite que o depurador se anexe ao aplicativo ASP.NET. VS define isso automaticamente quando você inicia a depuração, se você criou o projeto do modelo de projetos da Web.  
  
##  <a name="BKMK_Find_source_files"></a> Localizar arquivos de origem  
  
###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Onde o depurador procura por arquivos de origem  
 O depurador procura arquivos de origem nos seguintes locais:  
  
1.  Arquivos que estão abertos no IDE da instância do Visual Studio que iniciou o depurador.  
  
2.  Arquivos da solução que está aberto na instância do Visual Studio.  
  
3.  Diretórios que são especificados no **Propriedades comuns** \/ **depurar arquivos fonte** página nas propriedades da solução. \(No **Solution Explorer**, selecione o nó da solução, com o botão direito e selecione **propriedades**. \)  
  
4.  As informações de origem da. PDB do módulo. Isso pode ser o local do arquivo de origem quando o módulo foi criado, ou pode ser um comando para um servidor de origem.  
  
###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Localizar e carregar arquivos de origem com a fonte não \/ nenhum símbolo carregado páginas  
 Quando o depurador interrompe a execução em um local onde o arquivo de origem não está disponível, ele exibirá o **Nenhuma origem carregada** ou **Nenhum símbolo carregado** páginas que podem ajudá\-lo a localizar o arquivo de origem. O **Nenhum símbolo carregado** aparece quando o depurador não pode localizar um arquivo de símbolo \(. PDB\) para o arquivo executável concluir sua pesquisa. A página nenhum símbolo fornece opções para procurar o arquivo. Se o. PDB for encontrado depois que você executar uma das opções e o depurador pode recuperar o arquivo de origem usando as informações no arquivo de símbolos, a fonte será exibida. Caso contrário, um **Nenhuma origem carregada** página aparece que descreve o problema. A página exibe links de opções que podem executar ações que podem resolver o problema.  
  
###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Adicionar caminhos de pesquisa do arquivo de origem para uma solução  
 Você pode especificar uma rede ou diretórios locais para procurar por arquivos de origem.  
  
1.  Selecione a solução no Solution Explorer e escolha **propriedades** no menu de atalho.  
  
2.  Sob o **Propriedades comuns** nó, escolha **depurar arquivos fonte**.  
  
3.  Clique na pasta ![Ferramentas &#47; opções &#47; ícone de pasta&#47;símbolos de depuração](../debugger/media/dbg_tools_options_foldersicon.png "DBG\_Tools\_Options\_FoldersIcon") ícone. Texto editável aparece no **diretórios que contêm o código\-fonte** lista.  
  
4.  Adicione o caminho que você deseja pesquisar.  
  
 Observe que apenas o diretório especificado será pesquisado. Você deve adicionar entradas para todos os subdiretórios que deseja pesquisar.  
  
###  <a name="BKMK_Use_source_servers"></a> Usar servidores de origem  
 Quando não há nenhum código\-fonte no computador local ou o arquivo. PDB não coincide com o código\-fonte, você pode usar o servidor de origem para ajudar a depurar um aplicativo. Servidor de origem recebe solicitações de arquivos e retorna os arquivos reais. Servidor de origem é executado por meio de um arquivo DLL chamado SRCSRV. dll. Servidor de origem lê o arquivo. PDB do aplicativo, que contém ponteiros para o repositório de código fonte, bem como os comandos usados para recuperar o código\-fonte do repositório. Você pode limitar quais comandos têm permissão para serem executados do arquivo. PDB do aplicativo listando os comandos permitidos dentro de um arquivo chamado SRCSRV, que deve ser colocado no mesmo diretório que SRCSRV. dll e devenv.exe.  
  
> [!IMPORTANT]
>  Comandos arbitrários podem ser inseridos no arquivo. PDB do aplicativo, portanto certifique\-se de que colocar somente o que você deseja executar no arquivo SRCSRV. Qualquer tentativa de executar um comando não no arquivo srcsvr ini fará com que uma caixa de diálogo de confirmação aparecer. Para obter mais informações, consulte [Aviso de segurança: o depurador deve executar o comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nenhuma validação é feita em parâmetros de comando, portanto, tenha cuidado com comandos confiáveis. Por exemplo, se você confiar no cmd.exe, um usuário mal\-intencionado pode especificar parâmetros que tornaria o comando perigoso.  
  
 **Para habilitar o uso de um servidor de origem**  
  
1.  Certifique\-se de que você está em conformidade com as medidas de segurança descritas na seção anterior.  
  
2.  No menu **Ferramentas**, selecione **Opções**.  
  
     O **opções** caixa de diálogo é exibida.  
  
3.  No **depuração** nó, escolha **geral**.  
  
4.  Selecione o **Habilitar suporte de servidor de origem** caixa de seleção.  
  
     ![Ativar opções do servidor de origem](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG\_Options\_General\_EnableSrcSrvr\_checkbox")  
  
5.  \(Opcional\) Escolha o filho opções que você deseja.  
  
     Observe que ambos **Permitir que o servidor de origem para assemblies de confiança parcial \(somente gerenciado\)** e **sempre executar comandos do servidor de origem não confiável sem avisar** pode aumentar os riscos de segurança discutidos acima.  
  
## Consulte também  
 [Alterações no Visual Studio 2012 e 2013 de carregamento de símbolo remoto do .NET](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)