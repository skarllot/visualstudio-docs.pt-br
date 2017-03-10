---
title: "Option Strict On n&#227;o permite restringir em convers&#245;es impl&#237;citas de tipo entre o m&#233;todo &#39;&lt; methodname &gt;&#39; e delegar &#39;&lt; nomedelegado &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36663"
  - "vbc36663"
helpviewer_keywords: 
  - "BC36663"
ms.assetid: fefc7ab5-b587-4ff9-a6bc-4c4e5d4b6b29
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n&#227;o permite restringir em convers&#245;es impl&#237;citas de tipo entre o m&#233;todo &#39;&lt; methodname &gt;&#39; e delegar &#39;&lt; nomedelegado &gt;&#39;
Com `Option Strict` você não pode ter uma conversão de restrição entre o tipo de dados de um parâmetro em um representante e o parâmetro correspondente de uma função ou `Sub` atribuído a uma variável do tipo delegado. Por exemplo, o delegado de função `Del` tem um parâmetro do tipo `Integer`, e as funções `Conversion1`, `Conversion2`, e `Conversion3` têm um parâmetro de diferentes tipos numéricos.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String Function Conversion1(ByVal n As Integer) As String Return "Valid" End Function Function Conversion2(ByVal n As Long) As String Return "Valid" End Function Function Conversion3(ByVal n As Short) As String Return "Not valid" End Function  
```  
  
 Porque há uma conversão de ampliação de `Integer` para `Integer` e `Long`, as atribuições a seguir são válidas.  
  
```vb#  
' Valid. Dim funDel1 As Del = AddressOf Conversion1 Dim funDel2 As Del = AddressOf Conversion2  
```  
  
 A conversão de `Integer` para `Short` é uma conversão de restrição. Portanto, a atribuição a seguir não é válida.  
  
```vb#  
' Not valid. Dim funDel3 As Del = AddressOf Conversion3  
```  
  
 ID do erro: BC36663  
  
### Para corrigir este erro  
  
-   Altere o tipo de dados do parâmetro em que o representante ou o método para que a relação de ampliação necessária exista.  
  
## Consulte também  
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)