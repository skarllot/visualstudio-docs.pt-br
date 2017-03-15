---
title: "CS1613 de erro do compilador | Microsoft Docs"
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
  - "CS1613"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1613"
ms.assetid: 9d7ea9c8-9953-459f-a3f0-c7e65d1b9f59
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1613 de erro do compilador
A classe de wrapper gerenciado coclass 'class' para interface ' de ' não pode ser encontrada \(uma referência de assembly está faltando?\)  
  
 Foi feita uma tentativa de instanciar um objeto COM de uma interface. A interface tem o **ComImport** e `CoClass` atributos, mas o compilador não pode localizar o tipo de dado para o `CoClass` atributo.  
  
 Para resolver esse erro, tente um destes procedimentos:  
  
-   Adicione uma referência ao assembly que tem o coclass \(na maioria das vezes que a interface e coclass devem estar no mesmo assembly\). Consulte [\/Reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option) ou [Add Reference Dialog Box](http://msdn.microsoft.com/pt-br/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) para obter informações.  
  
-   Corrigir o `CoClass` atributo na interface.  
  
 O exemplo a seguir demonstra o uso correto de **CoClassAttribute**:  
  
```  
// CS1613.cs using System; using System.Runtime.InteropServices; [Guid("1FFD7840-E82D-4268-875C-80A160C23296")] [ComImport()] [CoClass(typeof(A))] public interface IA{} public class A : IA {} public class AA { public static void Main() { IA i; i = new IA(); // This is equivalent to new A(). // because of the CoClass attribute on IA } }  
```