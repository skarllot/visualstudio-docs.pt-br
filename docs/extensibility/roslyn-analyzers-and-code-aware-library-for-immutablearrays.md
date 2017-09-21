---
title: "Analisadores de Roslyn e reconhecimento de código de biblioteca para ImmutableArrays | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 76cde01ecd3151fd29f848509dc1ca0518705b04
ms.lasthandoff: 02/22/2017

---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analisadores de Roslyn e reconhecimento de código de biblioteca para ImmutableArrays
O [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") ajuda a criar bibliotecas de código.  Uma biblioteca de código fornece funcionalidade que você pode usar e ferramentas (Roslyn analisadores) para ajudá-lo a usar a biblioteca da melhor maneira ou para evitar erros.  Este tópico mostra como criar um analisador de Roslyn do mundo real para capturar erros comuns ao usar o [NIB: coleções imutáveis](../Topic/NIB:%20Immutable%20Collections.md) pacote do NuGet.  O exemplo também demonstra como fornecer uma correção de código para um problema de código encontrado pelo analisador.  Os usuários veem código correções a lâmpada da interface do usuário do Visual Studio e podem aplicar uma correção para o código automaticamente.  
  
## <a name="getting-started"></a>Guia de Introdução  
 É necessário o seguinte para criar este exemplo:  
  
-   O Visual Studio 2015 (não uma edição Express) ou uma versão posterior.  Você pode usar o livre [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)  
  
-   [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  Você também pode, ao instalar o Visual Studio, verificar ferramentas de extensibilidade do Visual Studio em ferramentas comuns para instalar o SDK ao mesmo tempo.  Se você já tiver instalado o Visual Studio, você também pode instalar esse SDK, vá ao menu principal **arquivo | Novo | Projeto... **, escolhendo c# no painel de navegação esquerdo e, em seguida, extensibilidade.  Quando você escolhe o "**instalar as ferramentas de extensibilidade do Visual Studio**" modelo de projeto de navegação estrutural, solicitando que você baixe e instale o SDK.  
  
-   [.NET compiler Platform ("Roslyn") SDK](http://aka.ms/roslynsdktemplates).  Você também pode instalar esse SDK, vá ao menu principal **arquivo | Novo | Projeto... **, escolhendo **c#** no painel de navegação esquerdo e, em seguida, escolhendo **extensibilidade**.  Quando você escolhe "**baixar o SDK de plataforma do compilador .NET**" modelo de projeto de navegação estrutural, solicitando que você baixe e instale o SDK.  Esse SDK inclui o [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer).  Esta Ajuda da ferramenta extremamente útil descobrir quais tipos de modelo de código você deve procurar no seu analisador.  As chamadas de infraestrutura do analisador em seu código para tipos de modelo de código específico, para que seu código apenas executa quando necessário e pode se concentrar apenas na análise de código relevante.  
  
## <a name="whats-the-problem"></a>Qual é o problema?  
 Imagine que você fornecer uma biblioteca com ImmutableArray (por exemplo, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) suporte.</xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>  Os desenvolvedores de c# têm muita experiência com as matrizes do .NET.  No entanto, devido à natureza das técnicas de ImmutableArrays e otimização usada na implementação, intuitions de desenvolvedores do c# levar os usuários da sua biblioteca escrever códigos quebrados, conforme explicado abaixo.  Além disso, os usuários não veem seus erros até que o tempo de execução, o que não é a experiência de qualidade que são usados para no Visual Studio com .NET.  
  
 Os usuários estão familiarizados com a escrita de código semelhante ao seguinte:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Criação de matrizes vazias preencherem com linhas subsequentes de código e usando a sintaxe do inicializador de coleção são bastante familiares para os desenvolvedores de c#.  No entanto, o código para um ImmutableArray escrevendo o mesmo falhas em tempo de execução:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 O primeiro erro ocorre devido a ImmutableArray da implementação usando uma estrutura para encapsular o armazenamento de dados subjacente.  Estruturas devem ter construtores sem parâmetros para que `default(T)` expressões podem retornar todas as estruturas zero ou membros nulos.  Quando o código que acessa `b1.Length`, há uma tempo de execução cancelamento de referência nula erro porque não há nenhuma matriz de armazenamento subjacente na estrutura ImmutableArray.  É a maneira correta de criar um vazio ImmutableArray `ImmutableArray<int>.Empty`.  
  
 O erro com inicializadores de coleção acontece porque o método ImmutableArray.Add retorna novas instâncias de cada vez que é chamado.  Como ImmutableArrays nunca mudam, quando você adiciona um novo elemento, você obtém um novo objeto de ImmutableArray (que pode compartilhar o armazenamento por motivos de desempenho com um ImmutableArray preexistentes).  Porque `b2` aponta para o primeiro ImmutableArray antes de chamar `Add()` cinco vezes, `b2` é um padrão ImmutableArray.  Chamando comprimento nele também falhas com um valor nulo desreferência de erro.  A maneira correta de inicializar um ImmutableArray sem chamar o método Add manualmente é usar `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.  
  
## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Localizar tipos de nós de sintaxe relevante para acionar seu analisador  
 Para começar a criar o analisador, primeiro descobrir que tipo de SyntaxNode você precisa procurar.    Inicie o Visualizador de sintaxe no menu **exibir | Outras janelas | Visualizador do Roslyn Syntax**.  
  
 Coloque o cursor do editor na linha que declara `b1`.  Você verá o Syntax Visualizer mostra estão em um `LocalDeclarationStatement` nó da árvore de sintaxe.  Este nó tem um `VariableDeclaration`, que por sua vez tem uma `VariableDeclarator`, que por sua vez tem uma `EqualsValueClause`, finalmente, há um `ObjectCreationExpression`.  Ao clicar na árvore do Syntax Visualizer de nós, a sintaxe na janela do editor realça para mostrar o código representado por esse nó.  Os nomes dos tipos SyntaxNode sub correspondem aos nomes usados na gramática do c#.  
  
## <a name="creating-the-analyzer-project"></a>Criando o projeto do analisador  
 No menu principal, escolha **arquivo | Novo | Projeto... **.  No **novo projeto** caixa de diálogo, em **c#** projetos na barra de navegação à esquerda, escolha extensibilidade em no painel direito, escolha o **Analyzer com código corrigir** modelo de projeto.  Insira um nome e confirmar a caixa de diálogo.  
  
 O modelo é aberto um arquivo DiagnosticAnalyzer.cs.  Escolha esse editor guia de buffer.  Esse arquivo tem uma classe de analisador (formado do nome que você atribuiu o projeto) que deriva de `DiagnosticAnalyzer` (um tipo de Roslyn API).  A nova classe tem um `DiagnosticAnalyzerAttribute` declarar seu analisador é relevante para a linguagem c# para que o compilador detecta e carrega o analisador.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Você pode implementar um analisador usando o Visual Basic que se destina ao código c#, e vice-versa.  É mais importante em DiagnosticAnalyzerAttribute para escolher se o analisador direcionado para um idioma ou ambos.  Analisadores mais sofisticadas que exigem modelagem detalhada da linguagem podem direcionar apenas um único idioma.  Se o analisador, por exemplo, só verifica os nomes de tipo ou membro público, é possível usar o modelo de linguagem comum que roslyn oferece em Visual Basic e c#.  Por exemplo, o FxCop avisa que implementa uma classe <xref:System.Runtime.Serialization.ISerializable>, mas a classe não tem o <xref:System.SerializableAttribute>atributo é independente de linguagem e funciona em código do Visual Basic e c#.</xref:System.SerializableAttribute> </xref:System.Runtime.Serialization.ISerializable>  
  
## <a name="initalizing-the-analyzer"></a>Como inicializar o analisador  
 Role um pouco o `DiagnosticAnalyzer` classe para ver o `Initialize` método.  O compilador chama esse método ao ativar um analisador.  O método utiliza um `AnalysisContext` objeto que permite que seu analisador para obter informações de contexto e registrar retornos de chamada de eventos para os tipos de código que você deseja analisar.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Abrir uma nova linha neste método e o tipo de "contexto." Para ver uma lista de conclusão do Intellisense.  Você pode ver na lista de preenchimento, há muitas `Register…` métodos para lidar com vários tipos de eventos.  Por exemplo, o primeiro deles, `RegisterCodeBlockAction`, chamadas de volta ao seu código para um bloco, o que geralmente é código entre chaves.  Registrar-se para um bloco também chama de volta ao seu código para o inicializador de um campo, o valor atribuído a um atributo ou o valor de um parâmetro opcional.  
  
 Como outro exemplo, `RegisterCompilationStartAction`, chamadas de volta ao seu código no início de uma compilação, o que é útil quando você precisa coletar estado em vários locais.  Você pode criar uma estrutura de dados, digamos, para coletar todos os símbolos usados, e cada vez que o analisador é o retorno de chamada para alguns sintaxe ou símbolo, você pode salvar informações sobre cada local em sua estrutura de dados.  Quando você volta devido a fim de compilação, você pode analisar todos os locais que você salvou, por exemplo, para relatar os símbolos que usa o código de cada `using` instrução.  
  
 Usando o **Syntax Visualizer**, você sabe que você deseja ser chamado quando o compilador processa um ObjectCreationExpression.  Use este código para configurar o retorno de chamada:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 Você se registrar para um nó de sintaxe e filtrar somente objeto criação nós de sintaxe.  Por convenção, os autores de analisador usam uma lambda ao registrar ações, que ajuda a manter os analisadores sem monitoração de estado.  Você pode usar o recurso do Visual Studio **Generate From Usage** para criar o `AnalyzeObjectCreation` método.  Isso gera o tipo de parâmetro de contexto certo para você muito.  
  
## <a name="setting-properties-for-users-of-your-analyzer"></a>Propriedades de configuração para os usuários do seu analisador  
 Para que o analisador apareça na interface de usuário do Visual Studio adequadamente, procure e modifique a seguinte linha de código para identificar seu analisador:  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Change `"Naming"` to `"API Guidance"`.  
  
 Em seguida localize e abra o arquivo resx em seu projeto usando o **Solution Explorer**.  Você pode colocar uma descrição para o analisador, título, etc.  Você pode alterar o valor de todos eles para `“Don’t use ImmutableArray<T> constructor”` por enquanto.  Você pode colocar a cadeia de caracteres de formatação argumentos na cadeia de caracteres ({0}, \ {1 \, etc.) e posteriormente quando você chamar `Diagnostic.Create()`, você pode fornecer uma matriz params de argumentos a serem passados.  
  
## <a name="analyzing-an-object-creation-expression"></a>Analisar uma expressão de criação de objeto  
 O `AnalyzeObjectCreation` método usa um tipo diferente de contexto fornecido pela estrutura de analisador de código.  O método Initialize `AnalysisContext` permite registrar retornos de chamada de ação para configurar seu analisador.  O `SyntaxNodeAnalysisContext`, por exemplo, tem um `CancellationToken` que você pode passar ao redor.  Se um usuário começa a digitar no editor, o Roslyn cancelará analisadores em execução para salvar o trabalho e melhorar o desempenho.  Como outro exemplo, este contexto tem uma propriedade de nó que retorna o nó de sintaxe de criação do objeto.  
  
 Obtenha o nó, que pode assumir que é o tipo para o qual você filtrado a ação de nó de sintaxe:  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Iniciar o Visual Studio com o analisador na primeira vez  
 Inicie o Visual Studio, criando e executando seu analisador (pressione **F5**).  Porque a inicialização do projeto no **Solution Explorer** é o projeto do VSIX, executando suas compilações de código, seu código e um VSIX e, em seguida, inicia o Visual Studio com esse VSIX instalado.  Quando você inicia o Visual Studio dessa forma, ele inicia com um hive do registro distintos para que seu uso principal do Visual Studio não será afetado por suas instâncias de testes ao criar os analisadores.  Na primeira vez que você iniciar dessa forma, o Visual Studio faz várias inicializações semelhantes quando você primeiro iniciei o Visual Studio depois de instalá-lo.  
  
 Crie um projeto de console e, em seguida, insira o código de matriz para o método de principal de aplicativos de console:  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 As linhas de código com `ImmutableArray` tem rabiscos porque você precisa obter o pacote do NuGet imutável e adicionar um `using` instrução ao seu código.  Pressione o botão à direita do ponteiro no nó do projeto no **Solution Explorer** e escolha **Manage NuGet Packages... **.  No Gerenciador do NuGet, digite "Imutável" na caixa de pesquisa e escolha o item "System.Collections.Immutable" (não escolher "Microsoft.Bcl.Immutable") no painel esquerdo e pressione o botão instalar no painel à direita.  Instalando o pacote adiciona uma referência para as referências do projeto.  
  
 Você ainda verá rabiscos vermelhos em `ImmutableArray`, então colocar o cursor nesse identificador e pressione **CTRL +.** (ponto) para abrir o menu de correção sugerida e escolha Adicionar apropriado `using` instrução.  
  
 **Salve e feche** a segunda instância do Visual Studio por enquanto para colocá-lo em um estado limpo para continuar.  
  
## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Concluindo o analisador usando editar e continuar  
 Na primeira instância do Visual Studio, defina um ponto de interrupção no início de seu `AnalyzeObjectCreation` método pressionando **F9** com o cursor na primeira linha.  
  
 Inicie o seu analisador novamente com **F5**e a segunda instância do Visual Studio, reabra seu aplicativo de console é criada na última vez.  
  
 Retornar para a primeira instância do Visual Studio no ponto de interrupção porque o compilador Roslyn viu uma expressão de criação de objeto e chamadas para o seu analisador.  
  
 **Obter o nó de criação do objeto.** Passar sobre a linha que define o `objectCreation` variável pressionando **F10**e no **janela imediata** avaliar a expressão `“objectCreation.ToString()”`.  Você vê que a variável aponta para o nó de sintaxe é o código `"new ImmutableArray<int>()"`, apenas o que você está procurando.  
  
 **Obter ImmutableArray<> </> \> o objeto de tipo.** Você precisa verificar se o tipo que está sendo criado é ImmutableArray.  Primeiro, você obtém o objeto que representa esse tipo.  Verificar tipos usando o modelo semântico para garantir que você tem exatamente o tipo correto e não comparar a cadeia de caracteres de ToString ().  Digite a seguinte linha de código no final da função:  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Designar tipos genéricos em metadados com backquotes (') e o número de parâmetros genéricos.  Isso é porque você não vê "... ImmutableArray\<T > "no nome de metadados.  
  
 O modelo semântico tem muitas coisas úteis que permitem que você faça perguntas sobre símbolos, fluxo de dados, vida útil da variável, etc.  Roslyn separa os nós de sintaxe de modelo semântico por vários motivos engineering (desempenho, modelagem códigos incorretos, etc.).  Deseja que o modelo de compilação para procurar informações contidas nas referências para comparação de precisa.  
  
 Você pode arrastar o ponteiro de execução amarelo no lado esquerdo da janela do editor.  Arraste-o até a linha que define o `objectCreation` variável e passar sobre a nova linha de código usando **F10**.  Se você passar o ponteiro do mouse sobre a variável `immutableArrayOfType`, você vê que encontramos o tipo exato no modelo semântico.  
  
 **Obtenha o tipo da expressão de criação de objeto.** "Tipo" é usado em algumas maneiras neste artigo, mas isso significa que se você tiver "nova Foo" expressão, você precisa obter um modelo de Foo.  Você precisa obter o tipo da expressão de criação de objeto para ver se ele é o ImmutableArray\<T > tipo.  Use o modelo semântico novamente para obter informações de símbolo para o símbolo de tipo (ImmutableArray) na expressão de criação de objeto.  Digite a seguinte linha de código no final da função:  
  
```c#  
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;  
  
```  
  
 Porque seu analisador precisa lidar com código incompleto ou incorreto nos buffers de editor (por exemplo, há uma falta `using` instrução), você deve verificar por `symbolInfo` sendo `null`.  Você precisa obter um tipo nomeado (INamedTypeSymbol) do objeto de informações de símbolo para concluir a análise.  
  
 **Compare os tipos.** Como há um tipo genérico aberto de T que estamos procurando e o tipo no código é um tipo genérico concreto, consultar as informações de símbolo para que o tipo é construído a partir (um tipo genérico aberto) e comparar esse resultado com `immutableArrayOfTType`.  Digite o seguinte no final do método:  
  
```c#  
if (symbolInfo != null &&   
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))  
{}  
```  
  
 **Relatório de diagnóstico.** O diagnóstico de emissão de relatórios é muito fácil.  Use a regra criada no modelo de projeto, que é definido antes do método Initialize.  Como essa situação no código é um erro, você pode alterar a linha que inicializado regra substituir `DiagnosticSeverity.Warning` (Rabisco verde) com `DiagnosticSeverity.Error` (Rabisco vermelho).  Inicializa o resto da regra dos recursos que você editou próximo ao início do passo a passo.  Você também precisa informar o local para o rabisco, que é o local da especificação do tipo da expressão de criação de objeto.  Digite esse código de `if` bloco:  
  
```c#  
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));  
```  
  
 A função deve ser assim (talvez formatados de maneira diferente):  
  
```c#  
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)  
{  
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;  
    var immutableArrayOfTType =   
        context.SemanticModel  
               .Compilation  
               .GetTypeByMetadataName(  
                   "System.Collections.Immutable.ImmutableArray`1");  
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as  
        INamedTypeSymbol;  
    if (symbolInfo != null &&   
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))  
    {  
        context.ReportDiagnostic(  
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));  
    }  
}  
  
```  
  
 Remova o ponto de interrupção para que você possa ver seu trabalho analyzer (e parar de retornar para a primeira instância do Visual Studio).  Arraste o ponteiro de execução para o início do método e pressione **F5** continuar a execução.  Quando você voltar para a segunda instância do Visual Studio, o compilador será iniciado examinar o código novamente, e ele chamará seu analisador.  Você pode ver um rabisco em `ImmutableType<int>`.  
  
## <a name="adding-a-code-fix-for-the-code-issue"></a>Adicionando uma "correção de código" para o problema de código  
 Antes de começar, feche a segunda instância do Visual Studio e parar a depuração na primeira instância do Visual Studio (onde você está desenvolvendo o analyzer).  
  
 **Adicione uma nova classe.** Use o menu de atalho (botão de ponteiro à direita) no nó do projeto no Gerenciador de soluções e escolha Adicionar um novo item.  Adicione uma classe chamada `BuildCodeFixProvider`.  Essa classe deve derivar de `CodeFixProvider`, e você precisará usar **CTRL +.** (ponto) para invocar a correção de código que adiciona o correto `using` instrução.  Essa classe também precisa ser anotada com `ExportCodeFixProvider` atributo e você precisará adicionar uma `using` instrução para resolver o `LanguageNames` enum.  Você deve ter um arquivo de classe com o seguinte código:  
  
```c#  
using Microsoft.CodeAnalysis;  
using Microsoft.CodeAnalysis.CodeFixes;  
  
namespace ImmutableArrayAnalyzer  
{  
    [ExportCodeFixProvider(LanguageNames.CSharp)]  
    class BuildCodeFixProvider : CodeFixProvider  
    {}  
  
```  
  
 **Um stub membros derivados.** Agora, coloque o cursor do editor no identificador de `CodeFixProvider` e pressione **CTRL +.** (ponto) para a implementação para essa classe base abstrata de stub.  Isso gera uma propriedade e um método para você.  
  
 **Implemente a propriedade.** Preencha o `FixableDiagnosticIds` da propriedade `get` corpo com o código a seguir:  
  
```c#  
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);  
```  
  
 Roslyn reúne diagnósticos e correções combinando esses identificadores que são apenas cadeias de caracteres.  O modelo de projeto gerado uma ID de diagnóstico para você, e você é livre para alterá-lo.  O código na propriedade apenas retorna a ID da classe do analisador.  
  
 **O método RegisterCodeFixAsync usa um contexto.** O contexto é importante porque uma correção de código pode ser aplicadas a vários diagnóstico ou pode haver mais de um problema em uma linha de código.  Se você digitar "contexto". no corpo do método, a lista de preenchimento Intellisense mostrará alguns membros útil.  Há um membro CancellationToken que você pode verificar para ver se algo que deseja cancelar a correção.  Há um membro de documento que tem muitos membros úteis e permite que você obtenha a objetos de modelo de projeto e solução.  Há um Span membro que é o início e final do local do código especificado quando você relatou o diagnóstico.  
  
 **Definir o método assíncrono.** A primeira coisa que você precisa fazer é corrigir a declaração do método gerado para ser um `async` método.  A correção de código para arrancar a implementação de uma classe abstrata não inclui o `async` palavra-chave mesmo que o método retorna um `Task`.  
  
 **Obter a raiz da árvore de sintaxe.** Para modificar o código que necessário para produzir uma nova árvore de sintaxe com as alterações a correção de código faz.  É necessário o `Document` do contexto para chamar `GetSyntaxRootAsync`.  Isso é um método assíncrono porque há trabalho desconhecido para obter a árvore de sintaxe, incluindo possivelmente obtendo o arquivo de disco, analisá-lo e criar o modelo de código do Roslyn para ele.  UI do Visual Studio deve ser responsivo durante esse tempo, qual usando `async` permite.  Substitua a linha de código no método a seguir:  
  
```c#  
var root = await context.Document  
                        .GetSyntaxRootAsync(context.CancellationToken);  
```  
  
 **Localize o nó com o problema.** Você passa no período do contexto, mas o nó que você achar que talvez não seja o código que você precisa alterar.  O diagnóstico relatado fornecido apenas a extensão para o identificador de tipo (em que o Rabisco pertencia), mas você precisa substituir a expressão de criação de objeto inteiro, incluindo o `new` keywoard no início e os parênteses no final.  Adicione o seguinte código ao método (e usar **CTRL +.** Para adicionar um `using` instrução para `ObjectCreationExpressionSyntax`):  
  
```c#  
  
var objectCreation = root.FindNode(context.Span)  
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();  
```  
  
 **Registre a correção de código para a lâmpada da interface do usuário.** Quando você registra a correção de código, Roslyn encaixa a lâmpada da interface do usuário do Visual Studio automaticamente.  Os usuários finais verão usarem **CTRL +.** (ponto) quando o analisador rabisca uma má `ImmutableArray<T>` uso do construtor.  Como o provedor de correção de código é executado somente quando houver um problema, você pode assumir que a expressão de criação de objeto que estava procurando.  Do parâmetro de contexto, você pode registrar a nova correção de código, adicionando o seguinte código ao final do `RegisterCodeFixAsync` método:  
  
```c#  
  
context.RegisterCodeFix(  
            CodeAction.Create("Use ImmutableArray<T>.Empty",  
                              c => ChangeToImmutableArrayEmpty(objectCreation,  
                                                               context.Document,  
                                                               c)),  
            context.Diagnostics[0]);  
```  
  
 Você precisa colocar o cursor do editor no identificador de `CodeAction`, em seguida, use **CTRL +.** (ponto) para adicionar apropriado `using` instrução para esse tipo.  
  
 Em seguida, coloque o cursor do editor no `ChangeToImmutableArrayEmpty` identificador e uso **CTRL +.** novamente para gerar esse stub do método para você.  
  
 Este último trecho de código adicionado registra a correção de código, passando um `CodeAction` e a ID de diagnóstico para o tipo de problema encontrado.  Neste exemplo, há apenas um ID de diagnóstico que esse código fornece correções, portanto você pode apenas passar o primeiro elemento da matriz de IDs de diagnóstico.  Quando você cria o `CodeAction`, você passa o texto que deve usar a lâmpada da interface do usuário como uma descrição da correção do código.  Você também pode passar em uma função que usa um CancellationToken e retorna um novo documento.  O novo documento terá uma nova árvore de sintaxe que inclui o código corrigido que chama `ImmutableArray.Empty`.  Este trecho de código usa uma lambda para que ele pode fechar o nó objectCreation e documento do contexto.  
  
 **Construa a nova árvore de sintaxe.** No `ChangeToImmutableArrayEmpty` método cujo stub gerado anteriormente, digite a linha de código: `ImmutableArray<int>.Empty;`.  Se você exibir a janela da ferramenta Syntax Visualizer novamente, você pode ver que essa sintaxe é um nó de SimpleMemberAccessExpression.  Isso é o que esse método precisa construir e retornar em um novo documento.  
  
 A primeira alteração `ChangeToImmutableArrayEmpty` é adicionar `async` antes de `Task<Document>` porque os geradores de código não podem assumir o método deve ser assíncrona.  
  
 Preencha o corpo com o código a seguir para que o método é semelhante ao seguinte:  
  
```c#  
  
private async Task<Document> ChangeToImmutableArrayEmpty(  
    ObjectCreationExpressionSyntax objectCreation, Document document,  
    CancellationToken c)  
{  
    var generator = SyntaxGenerator.GetGenerator(document);  
    var memberAccess =   
        generator.MemberAccessExpression(objectCreation.Type, "Empty");  
    var oldRoot = await document.GetSyntaxRootAsync(c);  
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);  
    return document.WithSyntaxRoot(newRoot);  
}  
```  
  
 Você terá que colocar o cursor do editor `SyntaxGenerator` identificador e uso **CTRL +.** (ponto) para adicionar apropriado `using` instrução para esse tipo.  
  
 Esse código usa `SyntaxGenerator`, que é um tipo muito útil para a criação de novo código.  Depois de obter um gerador para o documento que tem o problema de código, `ChangeToImmutableArrayEmpty` chamadas `MemberAccessExpression`, passando o tipo que possui o membro que deseja acessar e passando o nome do membro como uma cadeia de caracteres.  
  
 Em seguida, o método busca a raiz do documento, e como isso pode envolver trabalho arbitrário em geral, o código aguarda essa chamada e passa o token de cancelamento.  Modelos de código Roslyn são imutáveis, semelhante a trabalhar com uma cadeia de caracteres do .NET; Quando você atualiza a cadeia de caracteres, obtenha um novo objeto de cadeia de caracteres de retorno.  Quando você chama `ReplaceNode`, você recebe um novo nó de raiz.  A maioria da árvore de sintaxe é compartilhado (porque é imutável), mas o `objectCreation` nó é substituído com o `memberAccess` nó, bem como todos os nós pai até a raiz da árvore de sintaxe.  
  
## <a name="trying-your-code-fix"></a>Testar a correção de código  
 Agora, você pode pressionar **F5** para executar o analisador em uma segunda instância do Visual Studio.  Abra o projeto de console usado anteriormente.  Agora você deve ver a lâmpada aparecer onde sua nova expressão de criação de objeto é para `ImmutableArray<int>`.  Se você pressionar **CTRL +.** (ponto final), em seguida, você verá seu código corrigir e você verá uma visualização de diferença do código gerado automaticamente na lâmpada da interface do usuário.  Roslyn cria para você.  
  
 Dica Pro: Se você iniciar a segunda instância do Visual Studio, e você não vê a lâmpada com a correção de código, em seguida, você precisará limpar o cache de componente do Visual Studio.  A limpeza do cache força o Visual Studio para examinar novamente os componentes para que o Visual Studio deve pegar seu componente mais recente.  Primeiro, desligue a segunda instância do Visual Studio.  No Windows Explorer, vá para seu diretório de usuário (c:\users\\<>\>) e encontre AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\.  Nesse diretório, exclua o subdiretório ComponentModelCache.  As alterações a versão com o Visual Studio "14".  
  
## <a name="talk-video-and-finish-code-project"></a>Vídeo de conversa e projetos de código de término  
 Você pode ver esse exemplo desenvolvido e discutido posteriormente [essa conversa](http://channel9.msdn.com/events/Build/2015/3-725).  A conversa demonstra o analisador de trabalho e orienta você criá-lo.  
  
 Você pode ver o código concluído [aqui](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers).  As subpastas DoNotUseImmutableArrayCollectionInitializer e DoNotUseImmutableArrayCtor possuem um arquivo c# para localizar problemas e um arquivo em c# que implementa as correções do código que aparecem na lâmpada da interface do usuário do Visual Studio.  Observe que o código concluído tem um pouco mais de abstração para evitar a busca de ImmutableArray\<T > tipo object repetidamente.  Ele usa ações registradas aninhadas para salvar o objeto de tipo em um contexto que está disponível sempre que as ações sub (analisar a criação do objeto e analisar inicializações de coleção) executar.  
  
## <a name="see-also"></a>Consulte também  
 [\\Palestra de \Build 2015](http://channel9.msdn.com/events/Build/2015/3-725)   
 [Código concluído no github](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)   
 [Vários exemplos no github, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)   
 [Outros documentos no site do github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)   
 [Regras FxCop implementadas com analisadores de Roslyn no github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
