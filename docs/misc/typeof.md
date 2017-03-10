---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Palavra-chave __typeof"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
**Observação** neste tópico se aplica somente à versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Consulte [typeid](/visual-cpp/windows/typeid-cpp-component-extensions) para obter informações sobre como usar a funcionalidade equivalente na nova sintaxe.  
  
 Retorna o **System:: Type** de um tipo especificado.  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 onde:  
  
 *typename*  
 O nome de um tipo gerenciado para o qual você deseja o **System:: Type** nome. Observe que um programa gerenciado, alguns tipos nativos tem tipo com alias no common language runtime. Por exemplo, `int` é um alias para **System:: Int32**.  
  
## Comentários  
 O **TypeOf** operador permite que você obtenha o **System:: Type** tipo de um tipo que você especificar.**TypeOf** também pode ser usado para retornar um valor de **System:: Type** em um bloco de atributo personalizado. Consulte [atributo](/visual-cpp/windows/attribute) para obter mais informações sobre como criar seus próprios atributos.  
  
## Exemplo  
 No exemplo a seguir, um atributo personalizado \(`AtClass`\) é aplicado a uma classe GC \(`B`\). O valor do atributo personalizado é recuperado com **TypeOf**:  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## Saída  
  
```  
in Type * constructor  
AtClass  
```