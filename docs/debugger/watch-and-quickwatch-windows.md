---
title: "Inspe&#231;&#227;o e Windows QuickWatch | Microsoft Docs"
ms.custom: ""
ms.date: "12/10/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.watch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "janela de inspeção de depuração [Visual Studio]"
  - "avaliar as expressões [depurador]"
  - "variáveis [depurador] avaliar"
  - "avaliação de expressão"
  - "registros, avaliar"
  - "depuração [Visual Studio], a avaliação de expressão"
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 45
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Inspe&#231;&#227;o e Windows QuickWatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar o **inspeção** \(**Debug \/ Windows \/ Assista \/ assistir \(1, 2, 3 e 4\)**\) e **QuickWatch** \(**Debug \/ QuickWatch**\) windows para inspecionar variáveis e expressões durante uma sessão de depuração. A diferença é que o **inspeção** janela pode exibir várias variáveis, enquanto o **QuickWatch** janela exibe uma única variável por vez.  
  
## Observando uma única variável com QuickWatch  
 Você pode usar o **QuickWatch** janela para observar uma única variável. Por exemplo, se você tiver o código a seguir:  
  
```c#  
static void Main(string[] args) { int a, b; a = 1; b = 2; for (int i = 0; i < 10; i++) { a = a + b; } }  
```  
  
 Você pode observar a uma variável na janela QuickWatch da seguinte maneira:  
  
1.  Definir um ponto de interrupção no `a = a + b;` linha.  
  
2.  Inicie a depuração. A execução pára no ponto de interrupção.  
  
3.  Abra o **QuickWatch** janela \(com o botão direito em a, escolha **Depurar \/ QuickWatch**, ou **SHIFT \+ F9**\). Você pode abrir a janela e adicionar a uma variável para o **expressão** janela, clique em **reavaliar**. Você deve ver a uma variável o **valores** janela, com um valor de 2.  
  
4.  O **QuickWatch** janela é uma janela de caixa de diálogo modal, portanto você não pode continuar a depuração enquanto ele está aberto. Você pode adicionar a variável para o **inspeção** janela clicando **Adicionar inspeção**.  
  
5.  Feche o **QuickWatch** janela. Agora você pode continuar a depuração enquanto você observar o valor de **inspeção** janela  
  
## Observando as variáveis com a janela de Observação  
 Você pode observar várias variáveis com o **inspeção** janela. Por exemplo, se você tiver o código a seguir:  
  
```c#  
static void Main(string[] args) { int a, b, c; a = 1; b = 2; c = 0; for (int i = 0; i < 10; i++) { a++; b *= 2; c = a + b; } }  
  
```  
  
 Adicione os valores das três variáveis à janela Inspeção da seguinte maneira:  
  
1.  Definir um ponto de interrupção no `c = a + b;` linha.  
  
2.  Iniciar a depuração \(**F5**\). A execução pára no ponto de interrupção.  
  
3.  Abra a janela Watch \(**Debug \/ Windows \/ Assista \/ Assista 1**, ou **CTRL \+ ALT \+ W, 1**\).  
  
4.  Adicionar o `a` variável para a primeira linha, o `b` variável na segunda linha e o `c` variável para a terceira linha.  
  
5.  Continue a depuração.  
  
 Você deve ver os valores da variável alterado conforme você itera através de `for` loop.  
  
 Se você estiver programando em código nativo, às vezes, você precisará qualificar o contexto de um nome de variável ou uma expressão contendo um nome de variável. O contexto é a função, arquivo de origem e módulo onde uma variável está localizada. Se você precisar fazer isso, você pode usar a sintaxe do operador de contexto. Para obter mais informações, consulte expressões em C\+\+.  
  
## Observando as expressões com a janela de Observação  
 Agora vamos tentar usar uma expressão em vez disso. Você pode adicionar qualquer expressão válida reconhecida pelo depurador.  
  
 Por exemplo, se você tiver o código listado na seção anterior, você pode obter a média dos três valores assim:  
  
 ![WatchExpression](../debugger/media/watchexpression.png "WatchExpression")  
  
 Em geral, as regras de avaliação de expressões no **inspeção** janela são as mesmas que as regras para avaliar expressões na linguagem de codificação. Se a expressão tiver um erro de sintaxe, você pode esperar o mesmo erro de compilador que você veria no editor de códigos. Aqui está um exemplo:  
  
 ![WatchExpressionError](~/debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Atualizando valores de inspeção estão desatualizados  
 Em determinadas circunstâncias, você poderá ver um ícone de atualização \(um círculo com duas setas ou um círculo com duas linhas onduladas\) quando uma expressão é avaliada no **inspeção** janela.  Por exemplo, se você tiver a avaliação da propriedade desativada \(**Ferramentas \/ opções \/ depuração \/ habilitar avaliação de propriedades e outras chamadas de função implícitas**\), e você tem o seguinte código:  
  
```c#  
static void Main(string[] args) { List<string> list = new List<string>(); list.Add("hello"); list.Add("goodbye"); }  
  
```  
  
 Se você definir um observador do `Count` propriedade da lista, você verá algo parecido com o seguinte:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Isso indica um erro ou um valor que está desatualizado. Geralmente você pode atualizar o valor clicando no ícone, mas em alguns casos você pode preferir não atualizá\-la. Primeiro, você precisa saber por que o valor não foi avaliado.  
  
 Se você apontar para o ícone, uma dica de ferramenta fornece informações sobre por que a expressão não foi avaliada. Se as setas de circundamento aparecerem, a expressão não foi avaliada para um dos seguintes motivos:  
  
-   •	Ocorreu um erro porque a expressão estava sendo avaliada. Por exemplo, pode ter ocorrido um tempo limite, ou uma variável pode ter ficado fora do escopo.  
  
-   •	A expressão contém uma chamada de função que pode disparar um efeito colateral do aplicativo \(consulte [Efeitos colaterais e expressões](#bkmk_sideEffects)\).  
  
-   A avaliação automática de propriedades e chamadas de função implícitas pelo depurador é desativada \(**Ferramentas \/ opções \/ depuração \/ habilitar avaliação de propriedades e outras chamadas de função implícitas**\), e, em seguida, a expressão não pode ser avaliada automaticamente.  
  
 Para atualizar o valor, clique no ícone de atualização ou pressione a barra de espaços. O depurador tenta reavaliar a expressão. Se o ícone de atualização apareceu porque a avaliação automática de propriedades e efeitos colaterais implícitos tiver foi desligada, a expressão pode ser avaliada.  
  
 Se você vir um ícone que é um círculo com duas linhas onduladas semelhantes a cordas, a expressão não foi avaliada devido à dependência potencial entre threads. Em outras palavras, avaliar o código requer que outros threads em seu aplicativo sejam executados temporariamente. Quando você estiver no modo de interrupção, todos os threads em seu aplicativo normalmente estão parados. Permitir que outros threads sejam executados temporariamente pode ter inesperado efeitos sobre o estado do seu programa e faz com que o depurador ignorar eventos como pontos de interrupção e as exceções geradas nesses threads.  
  
##  <a name="bkmk_sideEffects"></a> Efeitos colaterais e expressões  
 Avaliar algumas expressões pode alterar o valor de uma variável ou afetar o estado do programa. Por exemplo, avaliar a expressão a seguir altera o valor de `var1`:  
  
```  
var1 = var2  
```  
  
 Isso é chamado de um [efeito colateral](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efeitos colaterais podem tornar a depuração mais difícil alterando o modo de que operação do seu programa.  
  
 Uma expressão que é conhecida por ter efeitos colaterais é avaliada apenas uma vez, quando você primeiro inseri\-la. Avaliações subseqüentes são desativadas. Manualmente, você pode substituir esse comportamento, clicando no ícone de atualização que aparece ao lado do valor.  
  
 Uma maneira de evitar todos os efeitos colaterais é desativar a avaliação automática de funções \(**Ferramentas \/ opções \/ depuração \/ habilitar avaliação de propriedades e outras chamadas de função implícitas**\).  
  
 Quando a avaliação de propriedades ou chamadas de função implícitas é desativada, você pode forçar a avaliação usando o **CA** modificador de formato \(para c\# somente\). Consulte [Especificadores de formato em C\#](../debugger/format-specifiers-in-csharp.md).  
  
## Usando identificadores de objeto na janela Watch \(c\# e Visual Basic\)  
 Há momentos em que você deseja observar o comportamento de um objeto específico; Por exemplo, você talvez queira controlar um objeto referenciado por uma variável local depois que essa variável tiver saído do escopo. Em c\# e Visual Basic, você pode criar IDs para instâncias específicas de tipos de referência de objeto e usá\-los na janela de inspeção e em condições de ponto de interrupção. A ID do objeto é gerada, o common language runtime \(CLR\) serviços de depuração e associada ao objeto.  
  
> [!NOTE]
>  IDs de objeto criar referências fracas e não impede que o objeto seja coletado como lixo. Eles só são válidos para a sessão de depuração atual.  
  
 No código a seguir cria um método um `Person` usando uma variável local, mas você deseja descobrir o que o `Person`do nome é um método diferente:  
  
```c#  
class Person { public Person(string name) { Name = name; } public string Name { get; set; } } public class Program { List<Person> _people = new List<Person>(); public static void Main(string[] args) { MakePerson(); DoSomething(); } private static void MakePerson() { var p = new Person("Bob"); _people.Add(p); } private static void DoSomething() { // more processing Console.WriteLine("done"); } }  
  
```  
  
 Você pode adicionar uma referência à `Person` objeto o **inspeção** janela da seguinte maneira:  
  
1.  Defina um ponto de interrupção no código algum tempo depois que o objeto foi criado.  
  
2.  Iniciar a depuração e quando a execução parar no ponto de interrupção, localize a variável de **locais** janela, clique sobre ela e selecione **Criar ID de objeto**.  
  
3.  Você deve ver um **$** mais um número no **locais** janela. Isso é o ID do objeto.  
  
4.  Adicione a ID de objeto para a janela de observação.  
  
5.  Defina um ponto de interrupção em que você deseja observar o comportamento do objeto.  No código acima, que seria no `DoSomething()` método.  
  
6.  Continuar a depuração e execução parada no `DoSomething()` método, o **inspeção** janela exibe o `Person` objeto.  
  
> [!NOTE]
>  Se você deseja ver as propriedades do objeto, como `Person.Name` no exemplo acima, você deve habilitar avaliação da propriedade.  
  
## Usando os registros na janela Watch \(C\+\+\)  
 Se você estiver depurando código nativo, você pode adicionar nomes de registro, bem como nomes de variáveis usando **$\< nome do registro \>** ou **@\< registrar nome \>**.  Para obter mais informações, consulte [Pseudovariáveis](../debugger/pseudovariables.md).  
  
## DynamicView e a janela de Observação  
 Algumas linguagens de script \(por exemplo, JavaScript ou Python\) usam dinâmico ou [digitação pato](https://en.wikipedia.org/wiki/Duck_typing), e linguagens .NET \(na versão 4.0 e posterior\) oferece suporte a objetos que são difíceis de observar usando as janelas de depuração normais, porque eles podem ter métodos e propriedades de tempo de execução que não podem ser exibidos.  
  
 Quando a janela de observação exibe um ou um objeto criado a partir de um tipo que implementa o [IDynamicMetaObjectProvider Interface](../Topic/IDynamicMetaObjectProvider%20Interface.md), o depurador adiciona um especial **exibição dinâmica**  nó para o **Autos** exibir. Esse nó mostra os membros dinâmicos do objeto dinâmico, mas não permite editar os valores dos membros.  
  
 Se clicar duas vezes qualquer filho de um **exibição dinâmica** e escolha **Adicionar inspeção**, o depurador vai inserir uma nova variável de inspeção que converte um objeto em um objeto dinâmico. Em outras palavras, **nome do objeto** torna\-se \(**objeto \(dinâmico\)\). Nome**.  
  
 Avaliar os membros de um **exibição dinâmica** pode ter efeitos colaterais. Para obter uma explicação dos efeitos colaterais, consulte [Efeitos colaterais e expressões](#bkmk_sideEffects). Para c\#, o depurador não reavalia automaticamente os valores mostrados na **exibição dinâmica** quando você depura em uma nova linha de código. Para Visual Basic, as expressões são adicionados por meio de **exibição dinâmica** são atualizados automaticamente.  
  
 Para obter instruções sobre como atualizar os valores de exibição dinâmica, consulte [Atualizando valores de inspeção estão desatualizados](#bkmk_refreshWatch).  
  
 Se você quiser exibir apenas a **exibição dinâmica** para um objeto, você pode usar o **dinâmico** especificador de formato:  
  
-   C\#: **ObjectName, dinâmico**  
  
-   Visual Basic:: **$dynamic, ObjectName**  
  
 O **exibição dinâmica** também melhora a experiência de depuração para objetos COM. Quando o depurador encontrar um objeto COM envolvido no **ComObject**, ele adiciona um **exibição dinâmica** nó do objeto.  
  
## Consulte também  
 [Janelas do depurador](../debugger/debugger-windows.md)