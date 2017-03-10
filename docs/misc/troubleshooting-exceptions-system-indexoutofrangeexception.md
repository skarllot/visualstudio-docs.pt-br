---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IndexOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe IndexOutOfRangeException"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.IndexOutOfRangeException
Um <xref:System.IndexOutOfRangeException> exceção é lançada quando é feita uma tentativa de acessar um elemento de uma matriz ou coleção com um índice está fora dos limites da matriz ou menor que zero.  
  
## Dicas associadas  
 **Certifique\-se de que o índice máximo em uma lista é menor que o tamanho da lista**  
 O índice máximo em uma lista deve ser menor que o tamanho da lista.  
  
 **Verifique se que o índice não é um número negativo.**  
 Essa exceção será lançada se o índice é menor que zero.  
  
 **Verifique se os nomes de coluna de dados estão corretos.**  
 Essa exceção pode ser lançada se o nome da coluna de dados que está sendo fornecido para o <xref:System.Data.DataView.Sort%2A?displayProperty=fullName> propriedade não é válida. Para obter mais informações, consulte o <xref:System.Data.DataView> classe.  
  
## Exemplo  
  
### Descrição  
 O exemplo a seguir usa um `Try…Catch` bloco para interceptar o `IndexOutOfRangeException` quando o índice `i` está fora dos limites da matriz, 0 a 3. O exemplo exibe o seguinte:  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### Código  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## Consulte também  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Matrizes](/dotnet/visual-basic/programming-guide/language-features/arrays/index)