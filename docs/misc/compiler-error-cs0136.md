---
title: "CS0136 de erro do compilador | Microsoft Docs"
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
  - "CS0136"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0136"
ms.assetid: 379a1a7d-c52c-4f2b-9e77-c1107d26faf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0136 de erro do compilador
Uma variável local denominada 'var' não pode ser declarada nesse escopo porque ele deve gerar um significado diferente para 'var', que já é usado em um escopo 'pai ou filho\/atual' para denotar algo  
  
 Uma declaração de variável oculta outra declaração que seria no escopo. Renomear a variável é declarada na linha que gerou CS0136.  
  
## Exemplo  
 O exemplo a seguir gera CS0136:  
  
```  
// CS0136.cs  
namespace MyNamespace  
{  
   public class MyClass  
   {  
      public static void Main()  
      {  
         int i = 0;  
         {  
            char i = 'a';   // CS0136, hides int i  
         }  
         i++;  
      }  
   }  
}  
```  
  
 Do [Especificação da linguagem C\#](/dotnet/csharp/language-reference/language-specification), seção 7.5.2.1:  
  
 Para cada ocorrência de um determinado identificador como um nome simples em uma expressão ou declarador, dentro do espaço de declaração de variável local \(§3.3\) delimitador imediatamente dessa ocorrência, todas as outras ocorrências do mesmo identificador como um nome simples em uma expressão ou declarador devem se referir à mesma entidade. Essa regra garante que o significado de um nome é sempre o mesmo dentro de um determinado bloco, bloco de switch para\-, foreach \- ou instrução using ou função anônima.