---
title: "__property | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Palavra-chave __property"
  - "classes gerenciadas"
  - "classes de propriedades [C++], gerenciadas"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  Este tópico se aplica apenas a versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Consulte [property](/visual-cpp/windows/property-cpp-component-extensions) para obter informações sobre como usar a funcionalidade equivalente na nova sintaxe.  
  
 Declara a uma propriedade escalar ou indexada para a classe gerenciada.  
  
## Sintaxe  
  
```  
  
__property  
function-declarator  
  
```  
  
## Comentários  
 O `__property` apresenta a declaração de uma propriedade de palavra\-chave e pode aparecer em uma classe, interface ou tipo de valor. Uma propriedade pode ter uma função getter \(somente leitura\), uma função setter \(somente gravação\) ou ambos \(leitura\-gravação\).  
  
> [!NOTE]
>  Um nome de propriedade não pode corresponder ao nome da classe gerenciada que o contém. O tipo de retorno da função getter deve corresponder ao tipo do último parâmetro de uma função setter correspondente.  
  
## Exemplo  
 No exemplo a seguir, uma propriedade escalar \(`Size`\) é adicionado para o `MyClass` declaração. A propriedade é definida implicitamente e recuperada usando o `get_Size` e `set_Size` funções:  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## Saída  
  
```  
0  
4  
4  
```