---
title: "CS0135 de erro do compilador | Microsoft Docs"
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
  - "CS0135"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0135"
ms.assetid: 1bda402c-e8bd-4117-93d9-f4968d9e8303
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0135 de erro do compilador
'declaration1' está em conflito com a declaração 'declaration2'  
  
 O compilador não permite ocultar nomes, que geralmente leva a erros de lógica em seu código.  
  
## Exemplo  
 O exemplo a seguir gera CS0135:  
  
```  
// CS0135.cs  
public class MyClass2  
{  
   public static int i = 0;  
  
   public static void Main()  
   {  
      {  
         int i = 4;  
         i++;  
      }  
      i = 0;   // CS0135  
   }  
}  
```  
  
 Do [Especificação da linguagem C\#](/dotnet/csharp/language-reference/language-specification), seção 7.5.2.1:  
  
 Para cada ocorrência de um determinado identificador como um nome simples em uma expressão ou declarador, dentro do espaço de declaração de variável local \(§3.3\) delimitador imediatamente dessa ocorrência, todas as outras ocorrências do mesmo identificador como um nome simples em uma expressão ou declarador devem se referir à mesma entidade. Essa regra garante que o significado de um nome é sempre o mesmo dentro de um determinado bloco, bloco de switch para\-, foreach \- ou instrução using ou função anônima.