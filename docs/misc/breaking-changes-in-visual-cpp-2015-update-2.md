---
title: "Altera&#231;&#245;es significativas no Visual C++ 2015 atualiza&#231;&#227;o 2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5545ce3f-d8da-4007-88b7-8dba7dcd4d10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mithom"
---
# Altera&#231;&#245;es significativas no Visual C++ 2015 atualiza&#231;&#227;o 2
Ao atualizar para o Visual C\+\+ 2015 Update 2 CTP, você pode encontrar compilação e\/ou erros de tempo de execução no código compilado anteriormente e executado corretamente. Alterações no comportamento do compilador ou tempo de execução que causam tais problemas são conhecidas como *alterações significativas*, e normalmente são necessários pelas modificações no padrão da linguagem C\+\+, assinaturas de função ou o layout dos objetos na memória.  
  
 O restante deste artigo descreve alterações significativas específicas no Visual C\+\+ 2015 Update 2 CTP e neste artigo, o termos "novo comportamento" ou "agora" se referir a essa versão. Os termos "comportamento antigo" e "anterior" consultem atualização 1 do Visual C\+\+ 2015 e versões anteriores. Para obter informações sobre como quebrar as alterações que ocorreram entre a versão inicial do Visual C\+\+ 2015 e atualização 1 do Visual C\+\+ 2015, consulte [Alterações significativas na atualização 1](../misc/breaking-changes-in-visual-cpp-2015-update-1.md). Para obter informações sobre como quebrar as alterações que ocorreram entre o Visual C\+\+ 2013 e Visual C\+\+ 2015, consulte [Alterações significativas no Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Alterações significativas do compilador](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Compilador do Visual C\+\+  
  
-   **Erros e avisos adicionais podem ser emitidos como resultado da expressão SFINAE suporte parcial**  
  
     Versões anteriores do compilador não foram analisada determinados tipos de expressões dentro `decltype` especificadores devido à falta de suporte para a expressão SFINAE. Esse comportamento antigo estava incorreto e não de acordo com o padrão C\+\+. Agora, o compilador analisa essas expressões e tem suporte parcial a expressão SFINAE devido a melhorias contínuas de conformidade. Como resultado, o compilador agora emitirá avisos e erros encontrados nas expressões que versões anteriores do compilador não foram analisada.  
  
     Quando esse novo comportamento analisa um `decltype` expressão que inclui um tipo que não ainda foi declarado, o compilador emite o erro do compilador C2039 como resultado.  
  
 **erro C2039: *'type'*: não é um membro de *'namespace global '***     Exemplo 1: uso de um tipo não declarado \(antes\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  // error C2039  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     Exemplo 1 \(após\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename>  // forward declare s2struct s2;  
  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     Quando esse novo comportamento analisa um `decltype` expressão que está faltando um uso necessário o `typename` palavra\-chave para especificar um nome dependente é um tipo, o compilador emite aviso C4346 junto com o erro do compilador C2923 do compilador.  
  
 **Aviso C4346: *' S2 \< T \>:: tipo '*: nome dependente não é um tipo Erro C2923: *'s1'*: *' S2 \< T \>:: tipo '* não é um argumento de tipo de modelo válido para o parâmetro *' t '***     Exemplo 2: nome dependente não é um tipo \(antes\)  
  
    ```cpp  
    template <typename T>  
    struct s1  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    struct s2  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923  
    };  
    ```  
  
     Exemplo 2 \(após\)  
  
    ```cpp  
    template <typename T> struct s1 {...};  // as above  
    template <typename T> struct s2 {...};  // as above  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));  
    };  
    ```  
  
-   `volatile` **variáveis de membro impedir definidas implicitamente construtores e operadores de atribuição**  
  
     Versões anteriores do compilador permitiam uma classe que tem `volatile` variáveis de membro para ter padrão copiar\/mover construtores e padrão de operadores de atribuição de copiar\/mover gerados automaticamente. Esse comportamento antigo estava incorreto e não de acordo com o padrão C\+\+. Agora, o compilador considera uma classe que tem variáveis de membro volátil não triviais construção e operadores de atribuição que impede que as implementações padrão desses operadores gerados automaticamente.  Quando essa classe é um membro de uma união \(ou uma união anônima dentro de uma classe\), os construtores de copiar\/mover e copiar\/mover operadores de atribuição de união \(ou a classe que contém a união de unonymous\) serão implicitamente definidos como excluído. A tentativa de construir ou copie a união \(ou classe que contém a união anônima\) sem definir explicitamente\-los é um erro e o erro do compilador do compilador problemas C2280 como resultado.  
  
 **Erro C2280: *'B::B\(const B &\)'*: tentativa de fazer referência a uma função excluída**     Exemplo \(antes\)  
  
    ```cpp  
    struct A  
    {  
      volatile int i;  
      volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
      union  
      {  
        A a;  
        int i;  
      };  
    };  
  
    B b1 {*pa};  
    B b2 (b1);  // error C2280  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
    struct A  
    {  
      int i;int j;  
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
      A a;  
      a.i = pa->i;  
      a.j = pa->j;  
      return a;  
    }  
  
    struct B;  // as above  
  
    B b1 {GetA()};  
    B b2 (b1);  // error C2280  
    ```  
  
-   **Funções de membro estático não dão suporte a qualificadores cv.**  
  
     Versões anteriores do Visual C\+\+ 2015 permitiam funções de membro estático com qualificadores cv. Esse comportamento ocorre devido a uma regressão em Visual C\+\+ 2015 e Visual C\+\+ 2015 Update 1; Visual C\+\+ 2013 e versões anteriores do Visual C\+\+ rejeitam código escrito dessa maneira. O comportamento do Visual C\+\+ 2015 e atualização 1 do Visual C\+\+ 2015 está incorreto e não de acordo com o C\+\+ padrão.  Atualização 2 do Visual Studio 2015 rejeita código escrito dessa maneira e emite o erro do compilador C2511 em vez disso.  
  
 **Erro C2511: 'void A::func\(void\) const': função de membro não encontrada em 'A' sobrecarregada**     Exemplo \(antes\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     Exemplo \(após\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **Declaração de encaminhamento de enum não é permitida no código do WinRT** \(só afeta \/ZW\)  
  
     Código compilado para não permitir que o tempo de execução do Windows \(WinRT\) `enum` tipos para ser declarados, da mesma forma que quando o código C\+\+ gerenciado é compilado para o .net Framework usando o compilador \/clr alterna. Esse comportamento é garante que o tamanho de uma enumeração sempre é conhecido e pode ser projetado corretamente no sistema de tipos WinRT. O compilador rejeita código escrito dessa maneira e emite um erro do compilador C2599 junto com o erro do compilador C3197.  
  
 **Erro C2599: *'CustomEnum'*: não é permitida a declaração de encaminhamento de um enum do WinRT Erro C3197: *'public'*: só pode ser usado em definições**     Exemplo \(antes\)  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **Operador de não\-membro sobrecarregado novo e operador delete não podem ser declarados embutidos** \(nível 1 \(\/ W1\) ativado por padrão\)  
  
     Versões anteriores do compilador não emite um aviso quando o operador de não\-membro novo e funções do operador delete são declaradas embutidos. Código escrito dessa maneira é malformados \(nenhum diagnóstico necessário\) e pode causar problemas resultantes do novo incompatíveis e excluir operadores \(especialmente quando usado em conjunto com tamanho desalocação\) que podem ser difíceis de diagnosticar de memória.   O compilador agora emitirá C4595 para ajudar a identificar código escrito dessa forma de aviso do compilador.  
  
 **Aviso C4595: *'operator new'*: operador não\-membro novo ou excluir funções não podem ser declaradas embutidos**     Exemplo \(antes\)  
  
    ```cpp  
  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     Exemplo \(após\)  
  
    ```cpp  
  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     Corrigir o código escrito dessa maneira pode exigir que as definições de operador ser movidos para fora de um arquivo de cabeçalho e em um arquivo de origem correspondente.