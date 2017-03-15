---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ArgumentException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exceção ArgumentException"
  - "Exceção System.ArgumentException"
ms.assetid: d8052e62-bc73-4828-87e9-a84ef2a39a5b
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.ArgumentException
Um <xref:System.ArgumentException> exceção é lançada quando pelo menos um dos argumentos fornecidos para um método não atende às especificações dos parâmetros do método.  
  
 No exemplo a seguir, a exceção é lançada quando o argumento enviado ao método `DivideByTwo` não é um número par.  
  
```vb#  
Module Module1 Sub Main() ' ArgumentException is not thrown in DivideByTwo because 10 is ' an even number. Console.WriteLine("10 divided by 2 is {0}", DivideByTwo(10)) Try ' ArgumentException is thrown in DivideByTwo because 7 is ' not an even number. Console.WriteLine("7 divided by 2 is {0}", DivideByTwo(7)) Catch argEx As ArgumentException ' Tell the user which problem is encountered. Console.WriteLine("7 cannot be evenly divided by 2.") Console.WriteLine("Exception message: " & argEx.Message) End Try ' Uncomment the next statement to see what happens if you call ' DivideByTwo directly. 'Console.WriteLine(DivideByTwo(7)) End Sub Function DivideByTwo(ByVal num As Integer) As Integer ' If num is an odd number, throw an ArgumentException. The ' ArgumentException class provides a number of constructors ' that you can choose from. If num Mod 2 = 1 Then Throw New ArgumentException("Argument for num must be" & _ " an even number.") End If ' Value of num is even, so return half of its value. Return num / 2 End Function End Module  
```  
  
 Todas as instâncias de `ArgumentException` classe deve incluir informações que especificam qual argumento não é válido e qual é o intervalo de valores aceitáveis. Se uma exceção mais precisa, como <xref:System.ArgumentNullException> ou <xref:System.ArgumentOutOfRangeException>, com precisão descreve a situação, ele deve ser usado em vez de `ArgumentException`.  
  
 Para obter mais informações sobre essa exceção, incluindo exemplos em outros idiomas, consulte <xref:System.ArgumentException>. Para obter uma lista de construtores adicionais, consulte <xref:System.ArgumentException.%23ctor%2A>.  
  
## Consulte também  
 <xref:System.ArgumentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)