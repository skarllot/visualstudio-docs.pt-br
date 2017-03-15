---
title: "__nogc | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "declarações de tipo __nogc"
  - "classes [C++], tipo não gerenciado"
  - "classes não gerenciadas, a declaração de"
  - "classes não gerenciadas"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  Este tópico se aplica apenas a versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Na nova sintaxe, você não precisa marcar explicitamente um tipo como não gerenciado.  
  
 Declara explicitamente um tipo não gerenciado.  
  
## Sintaxe  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## Comentários  
 O `__nogc` palavra\-chave é usada para especificar explicitamente que um objeto é alocado no heap padrão C\+\+. Essa palavra\-chave é opcional. Se você não especificar `__gc` ou `__nogc` na frente de uma declaração de classe, o padrão é `__nogc`.  
  
 Objetos desse tipo são semelhantes aos objetos C\+\+ padrão são alocados do heap C\+\+ padrão e não estão sujeitos a restrições de um objeto gerenciado.  
  
 O `__nogc` palavra\-chave também é usado quando um objeto de um tipo Value alocado explicitamente no heap padrão C\+\+:  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  O `__nogc` palavra\-chave também pode ser aplicado a tipos de matriz e ponteiro.  
  
 Um ponteiro gc não pode ser um membro de um `__nogc` classe. Consulte [Value](../misc/value.md) para obter diretrizes sobre a incorporação de um tipo de valor em uma `__nogc` classe.  
  
## Exemplo  
 No exemplo a seguir, uma classe não gerenciada é declarada \(`X`\) e um objeto é instanciado e modificado:  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**