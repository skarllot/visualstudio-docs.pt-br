---
title: "CS1918 de erro do compilador | Microsoft Docs"
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
  - "CS1918"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1918"
ms.assetid: 9ad2cbbd-3c10-4d56-b4cd-385103d005d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1918 de erro do compilador
Membros da propriedade 'name' do tipo 'type' não pode ser atribuídos a um inicializador de objeto porque ele é de um valor de tipo.  
  
 Esse erro ocorre quando você tenta usar um inicializador de objeto para inicializar as propriedades de um tipo de estrutura que é uma propriedade da classe que está sendo inicializada.  
  
### Para corrigir este erro  
  
1.  Se você deve inicializar totalmente os campos de propriedade no inicializador de objeto, altere a estrutura para um tipo de classe. Caso contrário, inicialize os membros de struct em uma chamada de método separado depois de criar o objeto usando o inicializador de objeto.  
  
## Exemplo  
 O exemplo a seguir gera CS1918:  
  
```  
// cs1918.cs public struct MyStruct { public int i; } public class Test { private MyStruct str = new MyStruct(); public MyStruct Str { get { return str; } } public static int Main() { Test t = new Test { Str = { i = 1 } }; // CS1918 return 0; } }  
  
```  
  
## Consulte também  
 [Inicializadores de objeto e coleção](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)