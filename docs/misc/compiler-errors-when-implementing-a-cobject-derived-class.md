---
title: "Erros de compilador ao implementar uma classe derivada de CObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Compilando o código-fonte, classes derivadas de CObject"
  - "erros [C++]"
  - "erros [C++], o compilador"
  - "Classe de CObject, erros de compilador para classes derivadas"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Erros de compilador ao implementar uma classe derivada de CObject
Quando você implementa uma classe derivada de `CObject` e seu código é escrito de forma que o construtor de cópia ou operador de atribuição para a classe precisa ser chamado, o compilador pode relatar erros semelhantes ao seguinte:  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 Você pode reproduzir o problema ao compilar o exemplo na seção exemplo de código abaixo.  
  
> [!NOTE]
>  O exemplo de código mostrado neste artigo gera mensagens de erro a seguir:  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 A razão para os erros de compilador é que `CObject` declara um construtor particular de cópia e o operador de atribuição no arquivo AFX. h. Conseqüentemente, o compilador gera um construtor de cópia padrão e o operador de atribuição para o `CObject`\-classe derivada. Porque o compilador não encontra essas funções declaradas na classe, ele relata os erros.  
  
 Para evitar os erros do compilador, você precisa implementar um construtor de cópia e o operador de atribuição para o `CObject`\-classe derivada. Isso é ilustrado no exemplo de código abaixo. Você pode evitar os erros, removendo as linhas indicadas no código de exemplo.  
  
## Código de exemplo  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## Consulte também  
 [C4600 de avisos do compilador por meio de C4799](/visual-cpp/error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799)