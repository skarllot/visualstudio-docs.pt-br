---
title: "M&#233;todos an&#244;nimos e an&#225;lise de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "métodos anônimos, análise de código"
  - "análise de código, métodos anônimos"
  - "métodos, anônimos"
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos an&#244;nimos e an&#225;lise de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Um método anônimo* é um método que não tem nenhum nome.  Os métodos anônimas com mais frequência são usadas para passar um bloco de código como um parâmetro de delegação.  
  
 Este tópico explica como a análise de código trata os avisos e métrica que estão associados com os métodos anônimas.  
  
## Métodos anônimas declarados em um membro  
 Os avisos e métrica para um método anônima que é declarada em um membro, como um método ou um acessador, são associados ao membro que declara o método.  Não são associados ao membro que chama o método.  
  
 Por exemplo, na classe, todos os avisos que são encontrados na declaração de **anonymousMethod** devem ser gerados em **Method1** e não **Method2**.  
  
```vb#  
  
        Delegate Function ADelegate(ByVal value As Integer) As Boolean  
Class AClass  
  
    Sub Method1()  
        Dim anonymousMethod As ADelegate = Function(ByVal value As  Integer) value > 5  
        Method2(anonymousMethod)  
    End Sub Sub Method2(ByVal anonymousMethod As ADelegate)  
        anonymousMethod(10)  
    End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    void Method1()  
    {  
        Delegate anonymousMethod = delegate()   
        {   
          Console.WriteLine("");   
        }  
        Method2(anonymousMethod);  
    }  
  
    void Method2(Delegate anonymousMethod)  
    {  
        anonymousMethod();  
    }  
}  
```  
  
## Métodos anônimas embutidos  
 Avisos e métrica para um método anônima que é declarada como uma atribuição embutida para um campo é associada com o construtor.  Se o campo for declarado como `static` \(`Shared` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), avisos e métrica está associado ao construtor de classe; se não, são associados com o construtor da instância.  
  
 Por exemplo, na classe, todos os avisos que são encontrados na declaração de **anonymousMethod1** serão gerados no construtor padrão implicitamente gerado de **Classe**.  Enquanto isso, esses encontrados em **anonymousMethod2** serão aplicados no construtor implicitamente gerado da classe.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
Dim anonymousMethod1 As ADelegate = Function(ByVal value As     Integer) value > 5  
Shared anonymousMethod2 As ADelegate = Function(ByVal value As      Integer) value > 5  
  
Sub Method1()  
    anonymousMethod1(10)  
    anonymousMethod2(10)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod1 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    static Delegate anonymousMethod2 = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    void Method()  
    {  
       anonymousMethod1();  
       anonymousMethod2();  
    }  
}  
```  
  
 Uma classe pode conter um método anônima embutida que atribuísse um valor em um campo que tem mais bloqueadores.  Nesse caso, avisos e métrica são associados a todos os construtores a menos que cadeias do construtor para outro construtor na mesma classe.  
  
 Por exemplo, na classe, todos os avisos que são encontrados na declaração de **anonymousMethod** devem ser gerados em **Classe \(int\)** e **Classe \(cadeia de caracteres\)** mas não em **Classe \(\)**.  
  
```vb#  
  
    Delegate Function ADelegate(ByVal value As Integer) As Boolean Class AClass  
  
Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)   
value > 5  
  
Sub New()  
    New(CStr(Nothing))  
End Sub Sub New(ByVal a As Integer)  
End Sub Sub New(ByVal a As String)  
End Sub End Class  
```  
  
```c#  
  
        delegate void Delegate();  
class Class  
{  
    Delegate anonymousMethod = delegate()   
    {   
       Console.WriteLine("");   
    }  
  
    Class() : this((string)null)  
    {  
    }  
  
    Class(int a)  
    {  
    }  
  
    Class(string a)  
    {  
    }  
}  
```  
  
 Embora isso possa aparecer inesperado, isso ocorre porque a saída do compilador um método exclusivo para cada construtor que não chaining para outro construtor.  Devido a esse comportamento, qualquer violação que ocorra em **anonymousMethod** deve ser suprimida separadamente.  Isso também significa que se um novo construtor é introduzido, os avisos que foram suprimidos anteriormente em **Classe \(int\)** e **Classe \(cadeia de caracteres\)** também deve ser suprimido no novo construtor.  
  
 Você pode contornar esse problema em uma das duas maneiras.  Você pode declarar **anonymousMethod** em um construtor comuns que todos os construtores encadeassem.  Ou você pode declarar\-lo em um método de inicialização que é chamado por todos os construtores.  
  
## Consulte também  
 [Analisando a qualidade do código gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)