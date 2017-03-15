---
title: "Covari&#226;ncia de matriz | Microsoft Docs"
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
  - "matrizes [C++], covariância"
ms.assetid: 889fdde3-85fe-44d5-bf2d-d3d4aa14e746
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mithom"
manager: "douge"
---
# Covari&#226;ncia de matriz
Dada a classe de referência D com a classe base direta ou indireta B, uma matriz do tipo D pode ser atribuída a uma variável de matriz do tipo b.  
  
```  
// clr_array_covariance.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   // String derives from Object  
   array<Object^>^ oa = gcnew array<String^>(20);  
}  
```  
  
## Comentários  
 Uma atribuição a um elemento de matriz deve ter atribuições compatíveis com o tipo dinâmico da matriz. Uma atribuição a um elemento de matriz com tipo incompatível fará com que System::ArrayTypeMismatchException seja lançada.  
  
 Covariância de matriz não se aplica a matrizes de tipo de classe de valor. Por exemplo, as matrizes de Int32 não podem ser convertidas em objeto ^ matrizes, até mesmo por meio de conversão boxing.  
  
## Exemplo  
  
```  
// clr_array_covariance2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct Base { int i; };  
ref struct Derived  : Base {};  
ref struct Derived2 : Base {};  
ref struct Derived3 : Derived {};  
ref struct Other { short s; };  
  
int main() {  
   // Derived* d[] = new Derived*[100];  
   array<Derived^> ^ d = gcnew array<Derived^>(100);  
  
   // ok by array covariance  
   array<Base ^> ^  b = d;  
  
   // invalid  
   // b[0] = new Other;  
  
   // error (runtime exception)  
   // b[1] = gcnew Derived2;  
  
   // error (runtime exception),  
   // must be "at least" a Derived.  
   // b[0] = gcnew Base;  
  
   b[1] = gcnew Derived;  
   b[0] = gcnew Derived3;  
}  
```  
  
## Consulte também  
 [Arrays](/visual-cpp/windows/arrays-cpp-component-extensions)