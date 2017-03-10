---
title: "CS0313 de erro do compilador | Microsoft Docs"
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
  - "CS0313"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0313"
ms.assetid: a0b0f2fb-e742-4df8-98bd-3bc068f0c71c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0313 de erro do compilador
O tipo 'type1' não pode ser usado como tipo parâmetro 'nome do parâmetro' no genérico tipo ou método 'type2'. O tipo anulável 'type1' não satisfaz a restrição de 'type2'. Tipos anuláveis não podem atender a todas as restrições de interface.  
  
 Um tipo anulável não é equivalente à sua contraparte não\-nulo. No exemplo a seguir, `ImplStruct` satisfaz a `BaseInterface` restrição mas `ImplStruct?` não porque `Nullable<ImplStruct>` não implementa `BaseInterface`.  
  
### Para corrigir este erro  
  
1.  Usando o código a seguir como exemplo, uma solução é especificar um comum `ImplStruct` como o primeiro argumento de tipo na chamada para `TestMethod`. Modifique `TestMethod` para criar uma versão nula `Implstruct` na instrução de retorno:  
  
    ```  
    return new Nullable<T>(t);  
    ```  
  
## Exemplo  
 O código a seguir gera CS0313:  
  
```  
// cs0313.cs public interface BaseInterface { } public struct ImplStruct : BaseInterface { } public class TestClass { public T? TestMethod<T, U>(T t) where T : struct, U { return t; } } public class NullableTest { public static void Run() { TestClass tc = new TestClass(); tc.TestMethod<ImplStruct?, BaseInterface>(new ImplStruct?()); // CS0313 } public static void Main() { } }  
```  
  
## Consulte também  
 [Tipos anuláveis](/dotnet/csharp/programming-guide/nullable-types/index)