---
title: "__value | Microsoft Docs"
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
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Palavra-chave __value"
  - "tipos de valor, declarando"
  - "palavra-chave Value, sintaxe"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  Este tópico se aplica apenas a versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Consulte [Classes and Structs](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) para obter informações sobre como usar a funcionalidade equivalente na nova sintaxe.  
  
 Declara uma classe para ser um tipo Value.  
  
## Sintaxe  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## Comentários  
 Um `__value` difere do tipo `__gc` tipos em que `__value` variáveis de tipo contém diretamente seus dados, enquanto variáveis gerenciadas apontam para seus dados, que são armazenados no heap de common language runtime.  
  
 As condições a seguir se aplicam a `__value` tipos:  
  
-   O `__value` palavra\-chave não pode ser aplicada a uma interface.  
  
-   Um `__value` tipo pode herdar de qualquer número de interfaces e não pode herdar de outros tipos ou `__value` tipos.  
  
-   Um `__value` tipo é sealed por definição. Para obter mais informações, consulte [sealed](../misc/sealed.md).  
  
-   É válido usar um `__value` digitar em qualquer lugar que um tipo gerenciado é permitido.  
  
> [!NOTE]
>  O `__value` palavra\-chave não é permitida quando usada com a `__abstract` palavra\-chave.  
  
 Um `__value` tipo pode ser explicitamente conectado a um **System:: Object** ponteiro. Isso é conhecido como conversão boxing.  
  
 As diretrizes a seguir se aplicam à inserção de um tipo de valor dentro de uma `__nogc` tipo:  
  
-   O tipo de valor deve ter **LayoutSequential** ou **LayoutExplicit**.  
  
-   O tipo de valor não pode ter membros do ponteiro gc.  
  
-   O tipo de valor não pode ter membros de dados particulares.  
  
 Nas extensões gerenciadas para C\+\+, os equivalentes a uma classe c\# e uma estrutura c\# são:  
  
|Extensões gerenciadas do C\+\+|C\#|Para obter mais informações|  
|------------------------------------|---------|---------------------------------|  
|struct GC<br /><br /> \- ou \-<br /><br /> classe GC|classe|[classe](/dotnet/csharp/language-reference/keywords/class) palavra\-chave|  
|struct Value<br /><br /> \- ou \-<br /><br /> classe Value|struct|[struct](/dotnet/csharp/language-reference/keywords/struct) palavra\-chave|  
  
## Exemplo  
 No exemplo a seguir, um `__value` tipo \(`V`\) é declarado e, em seguida, duas instâncias do `__value` tipo são manipulados:  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```