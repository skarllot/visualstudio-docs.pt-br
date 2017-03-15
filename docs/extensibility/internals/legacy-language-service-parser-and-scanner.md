---
title: "Analisador de serviço de linguagem herdada e Scanner | Documentos do Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 136f7c5a77a0d6fad96fc1fe0e0e513f483df10f
ms.lasthandoff: 02/22/2017

---
# <a name="legacy-language-service-parser-and-scanner"></a>Scanner e Parser de serviço de linguagem herdada
O analisador é o coração do serviço de idioma. As classes de linguagem de estrutura de pacote gerenciado (MPF) exigem um analisador de linguagem para selecionar as informações sobre o código que está sendo exibido. Um analisador separa o texto em tokens léxicos e identifica os tokens de tipo e a funcionalidade.  
  
## <a name="discussion"></a>Discussão  
 Este é um método c#.  
  
```c#  
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
  
 Neste exemplo, os tokens são palavras e sinais de pontuação. Os tipos de tokens são da seguinte maneira.  
  
|Nome de token|Tipo de token|  
|----------------|----------------|  
|namespace, void público, classe, int|keyword|  
|=|operator|  
|{ } ( ) ;|delimitador|  
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|  
|MyNamespace|namespace|  
|MyClass|classe|  
|MyFunction|method|  
|arg1|parâmetro|  
|var1|variável local|  
  
 A função do analisador é identificar os tokens. Alguns podem ter mais de um tipo. Depois que o analisador identificou os tokens, o serviço de linguagem pode usar as informações para fornecer recursos úteis, como realce de sintaxe, correspondência de chaves e as operações do IntelliSense.  
  
## <a name="types-of-parsers"></a>Tipos de analisadores  
 Um analisador de serviço de linguagem não é o mesmo que um analisador usado como parte de um compilador. No entanto, esse tipo de analisador precisa usar um scanner e um analisador, da mesma forma como um analisador de compilador.  
  
-   Um scanner é usado para identificar os tipos de tokens. Essas informações são usadas para realce de sintaxe e identificar rapidamente os tipos de token que podem disparar outras operações, por exemplo, correspondência de chaves. Este scanner é representado pelo <xref:Microsoft.VisualStudio.Package.IScanner>interface.</xref:Microsoft.VisualStudio.Package.IScanner>  
  
-   Um analisador é usado para descrever as funções e o escopo dos tokens. Essas informações são usadas em operações de IntelliSense para identificar elementos de linguagem, como métodos, variáveis, parâmetros e declarações e fornecer listas de membros e assinaturas de método com base no contexto. Esse parser também é usado para localizar pares correspondentes de elemento de linguagem, como colchetes e parênteses. Esse analisador é acessado por meio do <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método de <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
 Como implementar um scanner e parser para seu serviço de linguagem cabe a você. Existem vários recursos que descrevem como analisadores funcionam e como escrever sua próprias analisador. Além disso, vários produtos gratuitos e comerciais estão disponíveis que ajudam na criação de um analisador.  
  
### <a name="the-parsesource-parser"></a>O analisador de ParseSource  
 Ao contrário de um analisador que é usado como parte de um compilador (onde os tokens são convertidos em alguma forma de código executável), um analisador de serviço de linguagem pode ser chamado por vários motivos diferentes e em vários contextos diferentes. Como implementar essa abordagem no <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método o <xref:Microsoft.VisualStudio.Package.LanguageService>classe cabe a você.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> É importante ter em mente que o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método pode ser chamado em um thread em segundo plano.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
> [!CAUTION]
>  O <xref:Microsoft.VisualStudio.Package.ParseRequest>estrutura contém uma referência para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>objeto.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Package.ParseRequest> Isso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>objeto não pode ser usado no thread de segundo plano.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Na verdade, muitas das classes base MPF não podem ser usadas no thread de segundo plano. Eles incluem o <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager>classes e qualquer outra classe que direta ou indiretamente se comunica com o modo de exibição.</xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.ViewFilter> </xref:Microsoft.VisualStudio.Package.Source>  
  
 Esse analisador normalmente analisa a hora do arquivo na primeira fonte inteira é chamado ou quando a análise razão valor de <xref:Microsoft.VisualStudio.Package.ParseReason>é fornecido.</xref:Microsoft.VisualStudio.Package.ParseReason> Chamadas subsequentes para o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método lidar com uma pequena parte do código analisado e podem ser executadas muito mais rapidamente, usando os resultados da operação de análise completo anterior.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> O <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método comunica os resultados da operação de análise por meio de <xref:Microsoft.VisualStudio.Package.AuthoringSink>e <xref:Microsoft.VisualStudio.Package.AuthoringScope>objetos.</xref:Microsoft.VisualStudio.Package.AuthoringScope> </xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> O <xref:Microsoft.VisualStudio.Package.AuthoringSink>objeto é usado para coletar informações por um motivo específico de análise, por exemplo, informações sobre as extensões de correspondência de chaves ou assinaturas de método que tenham listas de parâmetros.</xref:Microsoft.VisualStudio.Package.AuthoringSink> O <xref:Microsoft.VisualStudio.Package.AuthoringScope>fornece conjuntos de declarações e assinaturas de método e também suporte para ir para Avançado Editar opção (**ir para definição**, **ir para declaração**, **ir para a referência**).</xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
### <a name="the-iscanner-scanner"></a>O Scanner IScanner  
 Você também deve implementar um scanner que implemente <xref:Microsoft.VisualStudio.Package.IScanner>.</xref:Microsoft.VisualStudio.Package.IScanner> No entanto, porque este scanner funciona em uma base linha por linha através de <xref:Microsoft.VisualStudio.Package.Colorizer>classe, ela é normalmente mais fácil de implementar.</xref:Microsoft.VisualStudio.Package.Colorizer> No início de cada linha, MPF oferece o <xref:Microsoft.VisualStudio.Package.Colorizer>classe um valor a ser usado como uma variável de estado que é passada para o scanner.</xref:Microsoft.VisualStudio.Package.Colorizer> No final de cada linha, o scanner retorna a variável de estado atualizado. MPF armazena essas informações de estado para cada linha para que o scanner pode iniciar a análise de qualquer linha sem precisar iniciar no início do arquivo de origem. Essa verificação rápida de uma única linha permite que o editor fornecer comentários rápidos para o usuário.  
  
## <a name="parsing-for-matching-braces"></a>Análise de chaves correspondentes  
 Este exemplo mostra o fluxo de controle para corresponder a uma chave de fechamento digitado pelo usuário. Nesse processo, o scanner é usado para colorir também é usado para determinar o tipo de token e se o token pode disparar uma operação de correspondência de chaves. Se o disparador for encontrado, o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método é chamado para localizar a chave correspondente.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Por fim, as duas chaves são realçadas.  
  
 Mesmo que as chaves são usados nos nomes de gatilhos e analisar as razões, esse processo não é limitado a chaves reais. Há suporte para qualquer par de caracteres que é especificado para ser uma correspondência de par. Os exemplos incluem (e), \< e >, e [e].  
  
 Suponha que o serviço de linguagem oferece suporte a chaves correspondentes.  
  
1.  O usuário digita uma chave de fechamento (}).  
  
2.  A chave de abertura é inserido na posição do cursor no arquivo de origem e o cursor é avançado por um.  
  
3.  O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>método o <xref:Microsoft.VisualStudio.Package.Source>classe é chamada com a chave de fechamento digitado.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>  
  
4.  O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>chamadas de método de <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>método o <xref:Microsoft.VisualStudio.Package.Source>classe para obter o token na posição antes da posição atual do cursor.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> </xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Esse token corresponde da chave de fechamento tipado).  
  
    1.  O <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>chamadas de método o <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>método de <xref:Microsoft.VisualStudio.Package.Colorizer>objeto para obter todos os tokens na linha atual.</xref:Microsoft.VisualStudio.Package.Colorizer> </xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> </xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>  
  
    2.  O <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>chamadas de método de <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>método o <xref:Microsoft.VisualStudio.Package.IScanner>o texto da linha atual do objeto.</xref:Microsoft.VisualStudio.Package.IScanner> </xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> </xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>  
  
    3.  O <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>repetidamente o método chama o <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>método o <xref:Microsoft.VisualStudio.Package.IScanner>objeto para reunir todos os tokens de linha atual.</xref:Microsoft.VisualStudio.Package.IScanner> </xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> </xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>  
  
    4.  O <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>método chama um método particular no <xref:Microsoft.VisualStudio.Package.Source>de classe para obter o token que contém a posição desejada e passa na lista de tokens obtido o <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>método.</xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> </xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>  
  
5.  O <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>método procura um sinalizador de gatilho de token de <xref:Microsoft.VisualStudio.Package.TokenTriggers>no token que é retornado o <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>método; isto é, o token que representa a chave de fechamento).</xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> </xref:Microsoft.VisualStudio.Package.TokenTriggers> </xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>  
  
6.  Se o disparador do sinalizador de <xref:Microsoft.VisualStudio.Package.TokenTriggers>for encontrado, o <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>método o <xref:Microsoft.VisualStudio.Package.Source>classe é chamada.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> </xref:Microsoft.VisualStudio.Package.TokenTriggers>  
  
7.  O <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>método inicia uma operação de análise com o valor do motivo de análise de <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Essa operação, por fim, chama o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método de <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Se analisar assíncrona estiver habilitado, esta chamada para o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método ocorre em um thread em segundo plano.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
8.  Quando a operação de análise é concluído, um manipulador de conclusão interno (também conhecido como um método de retorno de chamada) chamado `HandleMatchBracesResponse` é chamado na <xref:Microsoft.VisualStudio.Package.Source>classe.</xref:Microsoft.VisualStudio.Package.Source> Essa chamada é feita automaticamente pelo <xref:Microsoft.VisualStudio.Package.LanguageService>classe base não pelo analisador.</xref:Microsoft.VisualStudio.Package.LanguageService>  
  
9. O `HandleMatchBracesResponse` método obtém uma lista de intervalos da <xref:Microsoft.VisualStudio.Package.AuthoringSink>objeto armazenado na <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto.</xref:Microsoft.VisualStudio.Package.ParseRequest> </xref:Microsoft.VisualStudio.Package.AuthoringSink> (Uma marca span é um <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>estrutura que especifica um intervalo de linhas e caracteres no arquivo de origem.)</xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Esta lista de intervalos geralmente contém dois intervalos, cada uma para as chaves de abertura e fechamento.  
  
10. O `HandleBracesResponse` chamadas de método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>método o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>objeto armazenado na <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto.</xref:Microsoft.VisualStudio.Package.ParseRequest> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> Isso destaca as extensões determinadas.  
  
11. Se o <xref:Microsoft.VisualStudio.Package.LanguagePreferences>propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>estiver habilitado, o `HandleBracesResponse` método obtém o texto que é abrangido pela extensão de correspondência e exibe os primeiros 80 caracteres do que se estendem na barra de status.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> </xref:Microsoft.VisualStudio.Package.LanguagePreferences> Isso funcionará melhor se o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método inclui o elemento de linguagem que acompanha o par correspondente.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Para obter mais informações, consulte o <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>propriedade.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>  
  
12. Concluído.  
  
### <a name="summary"></a>Resumo  
 A operação de correspondência de chaves é normalmente limitada aos pares simples de elementos de linguagem. Elementos mais complexos, como correspondência triplos ("`if(…)`","`{`"e"`}`", ou "`else`","`{`"e"`}`"), pode ser realçada como parte de uma operação de conclusão do word. Por exemplo, quando a palavra "else" for concluída, a correspondência "`if`" instrução pode ser realçada. Se houvesse uma série de `if` / `else if` instruções, todos eles poderia ser destacadas, usando o mesmo mecanismo como chaves correspondentes. O <xref:Microsoft.VisualStudio.Package.Source>classe base já oferece suporte a isso, da seguinte maneira: O scanner deve retornar o valor do token gatilho <xref:Microsoft.VisualStudio.Package.TokenTriggers>combinado com o valor de disparador <xref:Microsoft.VisualStudio.Package.TokenTriggers>para o token antes da posição do cursor.</xref:Microsoft.VisualStudio.Package.TokenTriggers> </xref:Microsoft.VisualStudio.Package.TokenTriggers> </xref:Microsoft.VisualStudio.Package.Source>  
  
 Para obter mais informações, consulte [correspondência de chaves em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Análise de colorização  
 Coloração de código-fonte é simples, apenas identificar o tipo de token e retorno das informações de cores sobre esse tipo. O <xref:Microsoft.VisualStudio.Package.Colorizer>classe atua como intermediário entre o editor e o scanner para fornecer informações sobre todos os tokens de cor.</xref:Microsoft.VisualStudio.Package.Colorizer> O <xref:Microsoft.VisualStudio.Package.Colorizer>classe usa o <xref:Microsoft.VisualStudio.Package.IScanner>objeto para ajudar a coloração de uma linha e também para reunir informações de estado para todas as linhas no arquivo de origem.</xref:Microsoft.VisualStudio.Package.IScanner> </xref:Microsoft.VisualStudio.Package.Colorizer> Nas classes de serviço de linguagem MPF, a <xref:Microsoft.VisualStudio.Package.Colorizer>classe precisa ser substituída, pois ele se comunica com o scanner somente por meio de <xref:Microsoft.VisualStudio.Package.IScanner>interface.</xref:Microsoft.VisualStudio.Package.IScanner> </xref:Microsoft.VisualStudio.Package.Colorizer> Fornecer o objeto que implementa a <xref:Microsoft.VisualStudio.Package.IScanner>interface, substituindo o <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>método de <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> </xref:Microsoft.VisualStudio.Package.IScanner>  
  
 O <xref:Microsoft.VisualStudio.Package.IScanner>scanner tem uma linha de código-fonte por meio de <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>método.</xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> </xref:Microsoft.VisualStudio.Package.IScanner> Chama o <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>método são repetidas para obter o próximo token na linha até que a linha seja esgotada de tokens.</xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Para colorir, MPF tratará todo código-fonte como uma sequência de linhas. Portanto, o scanner deve ser capaz de lidar com chegando até ele como linhas de origem. Além disso, qualquer linha pode ser passada para o mecanismo de varredura a qualquer momento, e a única garantia é que o scanner recebe a variável de estado de linha antes da linha prestes a ser verificado.  
  
 O <xref:Microsoft.VisualStudio.Package.Colorizer>classe também é usada para identificar os gatilhos de token.</xref:Microsoft.VisualStudio.Package.Colorizer> Esses disparadores informam MPF que um token específico pode iniciar uma operação mais complexa, como preenchimento automático de palavras ou chaves correspondentes. Como identificar esses disparadores deve ser rápido e deve ocorrer em qualquer local, o scanner é mais adequado para essa tarefa.  
  
 Para obter mais informações, consulte [coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Análise de funcionalidade e escopo  
 Análise de funcionalidade e escopo requer mais do que apenas identificar os tipos de tokens que são encontrados. O analisador deve identificar não apenas o tipo de token, mas também a funcionalidade para a qual o token é usado. Por exemplo, um identificador é apenas um nome, mas em seu idioma, um identificador pode ser o nome de uma classe, namespace, método ou variável, dependendo do contexto. O tipo geral do token pode ser um identificador, mas o identificador também pode ter outros significados, dependendo do que e onde ela está definida. Essa identificação requer o analisador ter conhecimento mais amplo sobre o idioma que está sendo analisado. É aí que a <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe entra em cena.</xref:Microsoft.VisualStudio.Package.AuthoringSink> O <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe coleta informações sobre identificadores, métodos, pares correspondentes de idioma (como chaves e parênteses) e triplos de linguagem (semelhante a pares de idiomas, exceto que há três partes, por exemplo, "`foreach()`" "`{`"e"`}`").</xref:Microsoft.VisualStudio.Package.AuthoringSink> Além disso, você pode substituir o <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe para oferecer suporte a identificação de código, que é usada na validação inicial de pontos de interrupção para que o depurador não tem de ser carregado, e o **Autos** janela de depuração, que mostra parâmetros e variáveis locais automaticamente quando um programa está sendo depurado e requer o analisador para identificar parâmetros além daqueles que apresenta o depurador e variáveis locais apropriadas.</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
 O <xref:Microsoft.VisualStudio.Package.AuthoringSink>objeto é passado para o analisador como parte do <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto e um novo <xref:Microsoft.VisualStudio.Package.AuthoringSink>objeto é criada toda vez que um novo <xref:Microsoft.VisualStudio.Package.ParseRequest>objeto é criado.</xref:Microsoft.VisualStudio.Package.ParseRequest> </xref:Microsoft.VisualStudio.Package.AuthoringSink> </xref:Microsoft.VisualStudio.Package.ParseRequest> </xref:Microsoft.VisualStudio.Package.AuthoringSink> Além disso, o <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>método deve retornar um <xref:Microsoft.VisualStudio.Package.AuthoringScope>objeto, que é usado para manipular várias operações de IntelliSense.</xref:Microsoft.VisualStudio.Package.AuthoringScope> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> O <xref:Microsoft.VisualStudio.Package.AuthoringScope>objeto mantém uma lista de declarações e uma lista de métodos, ou que seja preenchido, dependendo do motivo para análise.</xref:Microsoft.VisualStudio.Package.AuthoringScope> O <xref:Microsoft.VisualStudio.Package.AuthoringScope>classe deve ser implementada.</xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Visão geral do serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-overview.md)   
 [Coloração de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Chave de correspondência em um serviço de linguagem herdado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
