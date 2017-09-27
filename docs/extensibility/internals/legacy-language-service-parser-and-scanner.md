---
title: "Analisador de serviço de linguagem herdados e Scanner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c95dbbeaf9dcd6e1014ce3d2af8a0398c6627fe3
ms.contentlocale: pt-br
ms.lasthandoff: 09/26/2017

---
# <a name="legacy-language-service-parser-and-scanner"></a>O scanner e o analisador de serviço de linguagem herdados
O analisador é o núcleo do serviço de linguagem. As classes de idioma gerenciado pacote MPF (estrutura) exigem um analisador de linguagem para selecionar as informações sobre o código que está sendo exibido. Um analisador separa o texto em símbolos lexicais e identifica os tokens de tipo e a funcionalidade.  
  
## <a name="discussion"></a>Discussão  
 Este é um método c#.  
  
```csharp  
namespace MyNamespace  
{  
    class MyClass  
    {  
        public void MyFunction(int arg1)  
        {  
            int var1 = arg1;  
        }  
    }  
}  
```  
  
 Neste exemplo, os tokens são as palavras e sinais de pontuação. Os tipos de tokens são da seguinte maneira.  
  
|Nome do token|Tipo de token|  
|----------------|----------------|  
|namespace nulo público, de classe, int|keyword|  
|=|operator|  
|{ } ( ) ;|delimitador|  
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|  
|MyNamespace|namespace|  
|MyClass|classe|  
|MyFunction|method|  
|arg1|parâmetro|  
|var1|variável local|  
  
 A função do analisador é identificar os tokens. Alguns podem ter mais de um tipo. Depois que o analisador identificou os tokens, o serviço de linguagem pode usar as informações para fornecer recursos úteis, como o realce de sintaxe, a correspondência de chaves e as operações do IntelliSense.  
  
## <a name="types-of-parsers"></a>Tipos de analisadores  
 Um analisador de serviço de linguagem não é o mesmo que um analisador usado como parte de um compilador. No entanto, esse tipo de analisador precisa usar um scanner e um analisador, da mesma forma como um analisador de compilador.  
  
-   Um scanner é usado para identificar tipos de tokens. Essas informações são usadas para realçar a sintaxe e para identificar rapidamente tipos de token que podem disparar outras operações, por exemplo, correspondência de chaves. Este scanner é representado pelo <xref:Microsoft.VisualStudio.Package.IScanner> interface.  
  
-   Um analisador é usado para descrever as funções e o escopo dos tokens. Essas informações são usadas em operações de IntelliSense para identificar elementos de linguagem, como métodos, variáveis, parâmetros e declarações e fornecem listas de membros e assinaturas de método com base no contexto. Esse parser também é usado para localizar pares correspondentes de elemento de linguagem, como colchetes e parênteses. Analisador é acessada por meio de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método o <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Como implementar um analisador e o scanner para o serviço de linguagem fica a seu critério. Existem vários recursos que descrevem como analisadores funcionam e como escrever sua próprias analisador. Além disso, se houver vários produtos gratuitos e comerciais que ajudam na criação de um analisador.  
  
### <a name="the-parsesource-parser"></a>O analisador de ParseSource  
 Ao contrário de um analisador que é usado como parte de um compilador (onde os tokens são convertidos em alguma forma de código executável), um analisador de serviço de idioma pode ser chamado por muitas razões diferentes e em vários contextos diferentes. Como implementar essa abordagem no <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método o <xref:Microsoft.VisualStudio.Package.LanguageService> classe fica a seu critério. É importante ter em mente que o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método pode ser chamado em um thread em segundo plano.  
  
> [!CAUTION]
>  O <xref:Microsoft.VisualStudio.Package.ParseRequest> estrutura contém uma referência para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto. Isso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto não pode ser usado no thread em segundo plano. Na verdade, muitas das classes base MPF não podem ser usadas no thread em segundo plano. Isso inclui o <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> classes e qualquer outra classe que direta ou indiretamente se comunica com o modo de exibição.  
  
 Esse parser normalmente analisa a hora de arquivo a primeira fonte inteira é chamado ou quando a análise razão valor de <xref:Microsoft.VisualStudio.Package.ParseReason> é fornecido. As chamadas subsequentes para o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método lidar com uma pequena parte do código analisada e pode ser executado mais rapidamente, usando os resultados da operação de análise completa anterior. O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método comunica-se os resultados da operação de análise por meio de <xref:Microsoft.VisualStudio.Package.AuthoringSink> e <xref:Microsoft.VisualStudio.Package.AuthoringScope> objetos. O <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto é usado para coletar informações por um motivo específico de análise, por exemplo, informações sobre as extensões de correspondência de chaves ou assinaturas de método com listas de parâmetros. O <xref:Microsoft.VisualStudio.Package.AuthoringScope> fornece coleções de declarações e assinaturas de método e também suporte para ir para as avançadas Editar opção (**ir para definição**, **ir para declaração**, **ir para Referência**).  
  
### <a name="the-iscanner-scanner"></a>O Scanner IScanner  
 Você também deve implementar um scanner que implementa <xref:Microsoft.VisualStudio.Package.IScanner>. No entanto, como este scanner opera em uma base linha por linha por meio de <xref:Microsoft.VisualStudio.Package.Colorizer> classe, ele é normalmente mais fácil de implementar. No início de cada linha, MPF fornece o <xref:Microsoft.VisualStudio.Package.Colorizer> um valor a ser usado como uma variável de estado que é passada para o scanner de classe. No final de cada linha, o scanner retorna a variável de estado atualizado. MPF armazena essas informações de estado para cada linha para que o scanner pode iniciar a análise de qualquer linha sem a necessidade de começar do início do arquivo de origem. Essa verificação rápida de uma única linha permite que o editor fornecer comentários rápido para o usuário.  
  
## <a name="parsing-for-matching-braces"></a>Análise de correspondência de chaves  
 Este exemplo mostra o fluxo de controle para correspondência de uma chave de fechamento que o usuário tiver digitado. Nesse processo, o scanner é usado para colorir também é usado para determinar o tipo de token e se o token pode disparar uma operação de correspondência de chaves. Se o gatilho for encontrado, o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método é chamado para localizar a chave correspondente. Por fim, as duas chaves são realçadas.  
  
 Mesmo que as chaves são usadas em nomes de gatilhos e analisar motivos, esse processo não é limitado a chaves reais. Há suporte para qualquer par de caracteres que é especificado para ser uma correspondência de par. Os exemplos incluem (e), \< e >, e [e].  
  
 Suponha que o serviço de linguagem dá suporte à correspondência de chaves.  
  
1.  O usuário digita uma chave de fechamento (}).  
  
2.  A chave é inserida na posição do cursor no arquivo de origem e o cursor é avançado por um.  
  
3.  O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método o <xref:Microsoft.VisualStudio.Package.Source> classe é chamada com a chave de fechamento digitada.  
  
4.  O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chamadas de método a <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método o <xref:Microsoft.VisualStudio.Package.Source> classe para obter o token na posição antes da posição atual do cursor. Esse token corresponde da chave de fechamento com tipo).  
  
    1.  O <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> chamadas de método de <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método o <xref:Microsoft.VisualStudio.Package.Colorizer> para obter todos os tokens na linha atual.  
  
    2.  O <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> chamadas de método de <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método o <xref:Microsoft.VisualStudio.Package.IScanner> o texto da linha atual do objeto.  
  
    3.  O <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> repetidamente o método chama o <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método no <xref:Microsoft.VisualStudio.Package.IScanner> objeto para coletar todos os tokens da linha atual.  
  
    4.  O <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método chama um método privado <xref:Microsoft.VisualStudio.Package.Source> de classe para obter o token que contém a posição desejada e passa na lista de tokens é obtido o <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> método.  
  
5.  O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> método procura um sinalizador de gatilho de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers> no token que é retornado o <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> método; isto é, o token que representa a chave de fechamento).  
  
6.  Se o gatilho do sinalizador de <xref:Microsoft.VisualStudio.Package.TokenTriggers> for encontrado, o <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método o <xref:Microsoft.VisualStudio.Package.Source> classe é chamada.  
  
7.  O <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> método inicia uma operação de análise com o valor do motivo de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>. Essa operação, por fim, chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método sobre o <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Se a análise assíncrona estiver habilitada, essa chamada para o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método ocorre em um thread em segundo plano.  
  
8.  Quando a operação de análise for concluída, um manipulador de conclusão interno (também conhecido como um método de retorno de chamada) chamado `HandleMatchBracesResponse` é chamado <xref:Microsoft.VisualStudio.Package.Source> classe. Esta chamada é realizada automaticamente pelo <xref:Microsoft.VisualStudio.Package.LanguageService> classe base não pelo analisador.  
  
9. O `HandleMatchBracesResponse` método obtém uma lista de intervalos da <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto armazenado na <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. (Um alcance é um <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> estrutura que especifica um intervalo de linhas e caracteres no arquivo de origem.) Esta lista de intervalos geralmente contém dois intervalos, um para as chaves de abertura e fechamento.  
  
10. O `HandleBracesResponse` chamadas de método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> método no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto armazenado na <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. Isso destaca as extensões determinadas.  
  
11. Se o <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> estiver habilitado, o `HandleBracesResponse` método obtém o texto contido pelo alcance de correspondência e exibe os primeiros 80 caracteres do que abrangem na barra de status. Isso funciona melhor se o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método inclui o elemento de linguagem que acompanha o par correspondente. Para obter mais informações, consulte a propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.  
  
12. Feito.  
  
### <a name="summary"></a>Resumo  
 A operação de correspondência de chaves geralmente é limitada a pares simples de elementos de linguagem. Elementos mais complexos, como correspondência triplos ("`if(...)`","`{`"e"`}`", ou "`else`","`{`"e"`}`"), pode ser realçado como parte de uma operação de conclusão do word. Por exemplo, quando a palavra "else" for concluída, a correspondência de "`if`" instrução pode ser realçada. Se houver uma série de `if` / `else if` instruções, todos eles podem ser realçadas usando o mesmo mecanismo como correspondência de chaves. O <xref:Microsoft.VisualStudio.Package.Source> classe base já oferece suporte para isso, da seguinte maneira: O scanner deve retornar o valor do token gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers> combinado com o valor de gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers> para o token que está antes da posição do cursor.  
  
 Para obter mais informações, consulte [correspondência de chaves em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Análise de colorização  
 Colorir o código-fonte é simples, apenas identificam o tipo de informações de cores de token e retorno sobre o tipo. O <xref:Microsoft.VisualStudio.Package.Colorizer> classe atua como intermediária entre o editor e o scanner para fornecer informações sobre todos os tokens de cor. O <xref:Microsoft.VisualStudio.Package.Colorizer> classe usa a <xref:Microsoft.VisualStudio.Package.IScanner> objeto para ajudar a coloração de uma linha e também para coletar informações de estado para todas as linhas no arquivo de origem. Nas classes de serviço de linguagem MPF, o <xref:Microsoft.VisualStudio.Package.Colorizer> classe não precisa ser substituída, pois ele se comunica com o scanner somente com o <xref:Microsoft.VisualStudio.Package.IScanner> interface. Fornecer o objeto que implementa o <xref:Microsoft.VisualStudio.Package.IScanner> interface, substituindo o <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> método o <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 O <xref:Microsoft.VisualStudio.Package.IScanner> scanner recebe uma linha do código-fonte por meio de <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> método. Chamadas para o <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> método são repetidas para obter o próximo token na linha até que a linha é esgotada de tokens. Para colorir, MPF trata todo o código de origem como uma sequência de linhas. Portanto, o scanner deve ser capaz de lidar com chegando até ele como linhas de origem. Além disso, qualquer linha pode ser passada para o scanner a qualquer momento e a garantia somente é que o scanner recebe a variável de estado de linha antes da linha prestes a ser verificado.  
  
 O <xref:Microsoft.VisualStudio.Package.Colorizer> classe também é usada para identificar os gatilhos de token. Esses disparadores informam MPF que um token específico pode iniciar uma operação mais complexa, como completar palavra ou correspondência de chaves. Como identificar tais gatilhos deve ser rápido e deve ocorrer em qualquer local, o scanner é mais adequado para essa tarefa.  
  
 Para obter mais informações, consulte [coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Análise de funcionalidade e escopo  
 Análise de funcionalidade e escopo requer pouco mais do que apenas identificar os tipos de tokens que são encontrados. O analisador deve identificar não apenas o tipo de token, mas também a funcionalidade para a qual o token é usado. Por exemplo, um identificador é apenas um nome, mas em seu idioma, um identificador pode ser o nome de uma classe, o namespace, o método ou a variável, dependendo do contexto. O tipo geral do token pode ser um identificador, mas o identificador também pode ter outros significados, dependendo do que é e onde ele está definido. Essa identificação requer o analisador ter conhecimento mais amplo sobre o idioma que está sendo analisado. Isso é onde o <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe entra. O <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe coleta informações sobre identificadores, métodos, pares correspondentes de idioma (como chaves e parênteses) e language triplos (semelhante a pares de idioma, exceto que há três partes, por exemplo, "`foreach()`" "`{`"e"`}`"). Além disso, você pode substituir o <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe para oferecer suporte à identificação de código, que é usada na validação inicial de pontos de interrupção para que o depurador não tem de ser carregado, e o **Autos** janela de depuração, que mostra o local variáveis e parâmetros automaticamente quando um programa está sendo depurado e requer o analisador para identificar apropriadas variáveis e parâmetros locais além daqueles que apresenta o depurador.  
  
 O <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto é passado para o analisador como parte do <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto e um novo <xref:Microsoft.VisualStudio.Package.AuthoringSink> objeto é criado toda vez que um novo <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto é criado. Além disso, o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método deve retornar um <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto, que é usado para tratar várias operações de IntelliSense. O <xref:Microsoft.VisualStudio.Package.AuthoringScope> objeto mantém uma lista de declarações e uma lista de métodos, ou que é preenchida, dependendo do motivo para análise. O <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe deve ser implementada.  
  
## <a name="see-also"></a>Consulte também  
 [Implementar um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Visão geral do serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-overview.md)   
 [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Correspondência de chave em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
