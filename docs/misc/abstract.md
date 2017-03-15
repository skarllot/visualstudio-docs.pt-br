---
title: "__abstract | Microsoft Docs"
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
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abstrato de classes [C++]"
  - "Palavra-chave __abstract"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  Este tópico se aplica apenas a versão 1 de Managed Extensions for C\+\+. Esta sintaxe só deve ser usada para manter o código da versão 1. Consulte [abstract](/visual-cpp/windows/abstract-cpp-component-extensions) para obter informações sobre como usar a funcionalidade equivalente na nova sintaxe.  
  
 Declara uma classe gerenciada que não pode ser instanciada diretamente.  
  
## Sintaxe  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## Comentários  
 O `__abstract` palavra\-chave declara que a classe de destino só pode ser usada como uma classe base de outra classe. Aplicando `__abstract` para uma classe ou estrutura não implica que o resultado é uma classe ou estrutura GC.  
  
 Diferente da noção de C\+\+ de um [abstrato](/visual-cpp/cpp/abstract-classes-cpp) classe base, uma classe com o `__abstract` palavra\-chave pode definir as funções de membro.  
  
> [!NOTE]
>  O `__abstract` palavra\-chave não é permitida quando usada com a `__value` ou `__sealed` palavra\-chave e é redundante quando usada com a `__interface` palavra\-chave.  
  
## Exemplo  
 No exemplo a seguir, a `Derived` classe é derivada de uma classe base abstrata \(`Base`\). Instanciação é tentada em ambos, mas apenas `Derived` for bem\-sucedida.  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```