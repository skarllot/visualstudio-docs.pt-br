---
title: "__sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "palavra-chave sealed [C++]"
  - "Palavra-chave __sealed"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  Este tópico se aplica apenas a versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Consulte [sealed](/visual-cpp/windows/sealed-cpp-component-extensions) para obter informações sobre como usar a funcionalidade equivalente na nova sintaxe.  
  
 Impede que uma classe seja uma classe base ou um método que está sendo substituído.  
  
## Sintaxe  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## Comentários  
 O `__sealed` palavra\-chave especifica que um método de classe não pode ser substituído ou que uma classe não pode ser uma classe base.  
  
 Ao usar o `__sealed` palavra\-chave, tenha os seguintes pontos em mente:  
  
-   Um `__sealed` método virtual não pode ser substituído.  
  
-   Se um método membro está marcado como `__sealed`, o `__sealed` qualificação é ignorada.  
  
-   Um `__sealed` método não pode ser puro.  
  
-   O **sealed** palavra\-chave não é permitida quando usada com a [interface](/visual-cpp/cpp/interface) palavra\-chave.  
  
 Quando uma classe \(ou struct\) é marcada com `__sealed`, a classe não pode ser usada como uma classe base. Por exemplo:  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  O `__sealed` palavra\-chave não é permitida quando usada com a `__abstract` palavra\-chave.  
  
## Exemplo  
 No exemplo a seguir, um método virtual lacrado \(`f`\) é declarada. A função é substituída, em seguida, em `main()`, causando um erro do compilador:  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```