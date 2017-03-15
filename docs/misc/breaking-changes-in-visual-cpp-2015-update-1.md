---
title: "Altera&#231;&#245;es significativas no Visual C++ 2015 atualiza&#231;&#227;o 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c0b1c2b-e1cf-4767-885b-b98df9b3730e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "mithom"
manager: "ghogen"
---
# Altera&#231;&#245;es significativas no Visual C++ 2015 atualiza&#231;&#227;o 1
Quando você atualizar para atualização 1 do Visual C\+\+ 2015, você pode encontrar compilação e\/ou erros de tempo de execução no código compilado anteriormente e executado corretamente. Alterações no comportamento do compilador ou tempo de execução que causam tais problemas são conhecidas como *alterações significativas*, e normalmente são necessários pelas modificações no padrão da linguagem C\+\+, assinaturas de função ou o layout dos objetos na memória.  
  
 O restante deste artigo descreve alterações significativas específicas na atualização 1 do Visual C\+\+ 2015 e neste artigo, o termos "novo comportamento" ou "agora" se referir a essa versão. Os termos "comportamento antigo" e "anterior" consultem a versão inicial do Visual Studio 2015 e versões anteriores. Para obter informações sobre como quebrar as alterações que ocorreram entre o Visual Studio 2013 e Visual Studio 2015, consulte [Alterações significativas no Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Alterações significativas do compilador](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Compilador do Visual C\+\+  
  
-   **Classes base virtuais privadas e herança indireta**  
  
     Versões anteriores do compilador permitiam uma classe derivada chame membro funções de seu *indiretamente derivado* `private virtual` classes base.  Esse comportamento antigo estava incorreto e não de acordo com o padrão C\+\+. O compilador não aceita código escrito dessa maneira e emite o erro do compilador C2280 como resultado.  
  
 **Erro C2280: *' void \* S3::\_\_delDtor\(unsigned int\)'*: tentativa de fazer referência a uma função excluída**     Exemplo \(antes\)  
  
    ```cpp  
    class base  
    {  
    protected:  
        base();  
        ~base();  
    };  
  
    class middle: private virtual base {};class top: public virtual middle {};  
  
    void destroy(top *p)  
    {  
        delete p;  //   
    }  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    class base;  // as above  
  
    class middle: protected virtual base {};  
    class top: public virtual middle {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
     \- ou \-  
  
    ```  
    class base;  // as above  
  
    class middle: private virtual base {};  
    class top: public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
-   **Operador sobrecarregado novo e operador delete**  
  
     Versões anteriores do compilador permitiam não\-membro `operator new` e não\-membro `operator delete` seja declarado estático e ser declarados em namespaces diferentes o namespace global.  Esse comportamento antigo criado um risco de que o programa não chama o `new` ou `delete` implementação do operador que o programador pretendia, resultando no comportamento de tempo de execução incorreta silenciosa. O compilador não aceita código escrito dessa maneira e emite o erro do compilador C2323 em vez disso.  
  
 **Erro C2323: *'operator new'*: operador não\-membro novo ou excluir funções não podem ser declaradas static ou em um namespace diferente do namespace global.**     Exemplo \(antes\)  
  
    ```cpp  
  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     Além disso, embora o compilador não fornece um diagnóstico específico, embutido operador novo é considerado malformados.  
  
-   **Chamar ' operador *tipo*\(\) ' \(conversão definida pelo usuário\) em tipos sem classe**  
  
     Versões anteriores do compilador permitido ' operador *tipo*\(\) ' seja chamado em tipos de classe não ignorando silenciosamente ele. Esse comportamento antigo criado um risco de geração de código de incorreto silenciosa, resultando em um comportamento imprevisível do tempo de execução. O compilador não aceita código escrito dessa maneira e emite o erro do compilador C2228 em vez disso.  
  
 **Erro C2228: à esquerda ' Operator *tipo*' deve ter a classe\/estrutura\/união**     Exemplo \(antes\)  
  
    ```cpp  
    typedef int index_t;  
  
    void bounds_check(index_t index);  
  
    void login(int column)  
    {  
        bounds_check(column.operator index_t());  // error C2228  
    }  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    typedef int index_t;  
  
    void bounds_check(index_t index);  
  
    void login(int column)  
    {  
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'  
    }  
    ```  
  
-   **Typename redundante em especificadores de tipo elaborados**  
  
     Versões anteriores do compilador permitido `typename` em um especificadores de tipo elaborado; código escrito dessa maneira é semanticamente incorreto. O compilador não aceita código escrito dessa maneira e emite o erro do compilador C3406 em vez disso.  
  
 **Erro C3406: 'typename' não pode ser usado em um especificador de tipo elaborado**     Exemplo \(antes\)  
  
    ```cpp  
    template <typename class T>  
    class container;  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case  
    class container;  
    ```  
  
-   **Dedução de tipo de matrizes de uma lista de inicializadores**  
  
     Versões anteriores do compilador não oferecia suporte a dedução de tipo de matrizes de uma lista de inicializadores. O compilador agora oferece suporte a essa forma de dedução de tipo e, como resultado, chamadas para modelos de função usando listas de inicializadores podem agora ser ambíguas ou uma sobrecarga diferente pode ser escolhida que nas versões anteriores do compilador. Para resolver esses problemas, o programa agora deve especificar explicitamente a sobrecarga que o programador pretendia.  
  
     Quando esse novo comportamento faz com que a resolução de sobrecarga de considerar um candidato adicional é igualmente tão bom quanto o candidato histórico, a chamada se torna ambígua e o compilador emite o erro do compilador C2668 como resultado.  
  
 **Erro C2668: '*função*': chamada ambígua para função sobrecarregada.**     Exemplo 1: Chamada ambígua para uma função sobrecarregada \(antes\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)  
    template <typename... Args>  
    void f(int, Args...);  //   
  
    template <int N, typename... Args>  
    void f(const int (&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now considers this call ambiguous, and issues a compiler error  
        f({3});  error C2668: 'f' ambiguous call to overloaded function  
    }  
    ```  
  
     Exemplo 1: chamada ambígua para uma função sobrecarregada \(após\)  
  
    ```cpp  
    template <typename... Args>  
    void f(int, Args...);  //   
  
    template <int N, typename... Args>  
    void f(const int (&)[N], Args...);  
  
    int main()  
    {  
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.  
        f(3);  
    }  
    ```  
  
     Quando esse novo comportamento faz com que a resolução de sobrecarga de considerar um candidato adicional que é uma correspondência melhor do que o candidato histórico, a chamada sem ambigüidade resolve para o novo candidato, causar uma alteração no comportamento do programa provavelmente será diferente do programador pretendido.  
  
     Exemplo 2: alterar a resolução de sobrecarga \(antes\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)  
    struct S  
    {  
        int i;  
        int j;  
    };  
  
    template <typename... Args>  
    void f(S, Args...);  
  
    template <int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead  
        f({1, 2});  
    }  
    ```  
  
     Exemplo 2: alterar a resolução de sobrecarga \(após\)  
  
    ```cpp  
    struct S;  // as before  
  
    template <typename... Args>  
    void f(S, Args...);  
  
    template <int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.  
        f(S{1, 2});  
    }  
    ```  
  
-   **Restauração de avisos de instrução switch**  
  
     Uma versão anterior do compilador removido previamente existente avisos relacionados a `switch` instruções; esses avisos agora foram restaurados. O compilador agora emitirá avisos restaurados e agora são emitidos avisos relacionados a casos específicos \(incluindo o caso padrão\) na linha que contém o caso ofensivo, em vez de na última linha da instrução switch. Como resultado de emissão agora esses avisos em linhas diferentes do que no passado, avisos anteriormente suprimidos usando `#pragma warning(disable:####)` não pode ser suprimido conforme o esperado. Para suprimir esses avisos conforme o esperado, talvez seja necessário mover o `#pragma warning(disable:####)` diretriz para uma linha acima do primeiro caso potencialmente ofensivos. A seguir estão os avisos restaurados.  
  
 **Aviso C4060: instrução switch contém sem rótulos 'casos' ou 'default' Aviso C4061: enumerador '*bit1*'no comutador de enum'*sinalizadores*' não é tratado explicitamente por um rótulo case Aviso C4062: enumerador '*bit1*'no comutador de enum'*sinalizadores*' não é tratado Aviso C4063: caso '*bit32*'não é um valor válido para a opção de enum'*sinalizadores*' Aviso C4064: opção de enum incompleta '*sinalizadores*' Aviso C4065: instrução switch contém 'padrão', mas sem rótulos 'case' Aviso C4808: caso '*valor*'não é um valor válido para a condição de comutador do tipo'*bool*' Aviso C4809: a instrução switch tem rótulo redundante 'default'; recebem todas as possíveis rótulos 'case'**     Exemplo de C4063 \(antes\)  
  
    ```cpp  
    class settings  
    {  
    public:  
        enum flags  
        {  
            bit0 = 0x1,  
            bit1 = 0x2,  
            ...  
        };  
        ...  
    };  
  
    int main()  
    {  
        auto val = settings::bit1;  
  
        switch (val)  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
        case settings::bit0 | settings::bit1:  // warning C4063  
            break;  
        }  
    };  
    ```  
  
     Exemplo de C4063 \(após\)  
  
    ```cpp  
    class settings {...};  // as above  
  
    int main()  
    {  
        // since C++11, use std::underlying_type to determine the underlying type of an enum  
        typedef std::underlying_type<settings::flags>::type flags_t;  
  
        auto val = settings::bit1;  
  
        switch (static_cast<flags_t>(val))  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
        case settings::bit0 | settings::bit1:  // ok  
            break;  
        }  
    };  
    ```  
  
     São fornecidos exemplos dos outros avisos restaurados em sua documentação.  
  
-   **\#include: uso do especificador do diretório pai '.. ' no caminho** \(\/Wall \/WX afeta somente\)  
  
     Versões anteriores do compilador não detectou o uso do especificador de diretório pai '.. ' no caminho de  `#include` diretivas. Código escrito dessa maneira geralmente se destina a incluir cabeçalhos que existem fora do projeto usando caminhos relativos de projeto incorretamente. Esse comportamento antigo criado um risco de que o programa foi compilado, incluindo um arquivo de origem diferente que o programador pretendido, ou que esses caminhos relativos não seria portáteis para outros ambientes de compilação. Agora o compilador detecta e notifica o programador de código escrito dessa maneira e emite um aviso C4464, do compilador opcional se habilitado.  
  
 **Aviso C4464: relativo ao caminho de inclusão contém '.. '**     Exemplo \(antes\)  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     Além disso, embora o compilador não dá um diagnóstico específico, também é recomendável que o especificador do diretório pai ".." Observação deve ser usada para especificar seu projeto diretórios de inclusão.  
  
-   **\#pragma optimize\(\) ultrapassa o fim do arquivo de cabeçalho** \(\/Wall \/WX afeta somente\)  
  
     Versões anteriores do compilador não detectou alterações nas configurações de sinalizador de otimização que escapam de um arquivo de cabeçalho incluído dentro de uma unidade de conversão. O compilador agora detecta e notifica o programador de código escrito dessa maneira e emite um aviso C4426 no local do ofensivo do compilador opcional `#include`, se habilitado. Esse aviso é emitido apenas se as alterações estão em conflito com os sinalizadores de otimização definido pelos argumentos de linha de comando para o compilador.  
  
 **Aviso C4426: alterados após incluir o cabeçalho, os sinalizadores de otimização pode ser devido a \#pragma optimize\(\)**     Exemplo \(antes\)  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
    ...  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  // warning C4426  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
    ...  
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  
    ```  
  
-   **Incompatíveis \#pragma warning\(push\)** e **\#pragma warning\(pop\)** \(afeta apenas \/Wall \/WX\)  
  
     versões anteriores do compilador não detectou `#pragma warning(push)` muda de estado sendo combinados com `#pragma warning(pop)` estado alterações em um arquivo de origem diferente, que raramente se destina. Esse comportamento antigo criado um risco de que o programa deve ser compilado com um conjunto diferente de avisos habilitado que o programador pretendido, possivelmente, resultando no comportamento de tempo de execução incorreta silenciosa. O compilador agora detecta e notifica o programador de código escrito dessa maneira e emite um aviso C5031 ao local onde a correspondência do compilador opcional `#pragma warning(pop)`, se habilitado. Esse aviso inclui uma observação a fazer referência ao local do correspondente warning\(push\) \#pragma.  
  
 **Aviso C5031: \#pragma warning\(pop\): incompatibilidade de probabilidade, popping o estado de aviso enviado em outro arquivo**     exemplo \(antes\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h ... #pragma warning(pop)  // pops a warning state not pushed in this source file ... // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling' ... #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031 ...   
    ```  
  
     exemplo \(após\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop)  // pops the warning state pushed in this source file // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h #pragma warning(push)  // pushes the warning state pushed in this source file #pragma warning(disable:####) ... #pragma warning(pop) // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order. ... #include "C5031_part2.h" ...   
    ```  
  
     Embora incomum, código escrito dessa forma, às vezes, é intencional. Código escrito dessa maneira é sensível às alterações na `#include` ordem; quando possível, recomendamos que os arquivos de código fonte gerenciar o estado de aviso de forma independente.  
  
-   **\#Pragma warning\(push\)** \(\/Wall \/WX afeta somente\)  
  
     Versões anteriores do compilador não detectou incomparável `#pragma warning(push)` alterações no final de uma unidade de conversão de estado. Agora o compilador detecta e notifica o programador de código escrito dessa maneira e emite um aviso C5032 no local do warning\(push\) \#pragma incomparável, do compilador opcional se habilitado. Esse aviso é emitido somente se não houver nenhum erro de compilação na unidade de tradução.  
  
 **Aviso C5032: detectado warning\(push\) \#pragma com nenhuma warning\(pop\) \#pragma correspondente**     Exemplo \(antes\)  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    // C5032.h ends without #pragma warning(pop)  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop) // matches #pragma warning (push) on line 1  
    // C5032.h ends  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **Avisos adicionais podem ser emitidos como resultado de rastreamento de estado de aviso \#pragma aprimorada**  
  
     Versões anteriores do compilador rastreadas \#pragma aviso alterações de estado insuficientemente bem ao problema que tudo isso avisos. Esse comportamento criado um risco que certos avisos suprimidos seriam efetivamente em circunstâncias diferentes que o programador pretendido. O compilador agora controla o estado de aviso \#pragma mais robustez – especialmente com relação às alterações de estado de aviso \#pragma dentro de modelos – e, opcionalmente, emite avisos novo C5031 e C5032 que se destinam a ajudar o programador Localizar usos não intencionais de `#pragma warning(push)` e `#pragma warning(pop)`.  
  
     Como resultado \#pragma aprimorado, rastreamento, avisos suprimidos anteriormente incorretamente ou avisos relacionados a problemas anteriormente misdiagnosed de alteração de estado de aviso agora pode ser emitido.  
  
-   **Identificação aprimorada de código inacessível**  
  
     Alterações de biblioteca padrão C\+\+ e maior capacidade de chamadas de função embutida em relação às versões anteriores do compilador podem permitir que o compilador provar que determinados códigos agora está inacessível. Esse novo comportamento pode resultar em novos e mais frequentemente emitido instâncias de aviso C4720.  
  
 **Aviso C4720: código inacessível**     Em muitos casos, esse aviso só pode ser emitido durante a compilação com otimizações habilitadas, desde otimizações pode inline mais chamadas de função, eliminar o código supérfluo ou caso contrário tornam possível determinar que certos tipos de código está inacessível. Temos observado que novas instâncias de aviso C4720 frequentemente ocorreram em blocos try\/catch, especialmente em relação ao uso de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).  
  
     Exemplo \(antes\)  
  
    ```cpp  
    try   
    {   
        auto iter = std::find(v.begin(), v.end(), 5);   
    }   
    catch(…)   
    {   
        do_something();  // ok   
    }  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    try   
    {   
        auto iter = std::find(v.begin(), v.end(), 5);   
    }   
    catch(…)   
    {   
        do_something();  // warning C4702: unreachable code  
    }  
    ```