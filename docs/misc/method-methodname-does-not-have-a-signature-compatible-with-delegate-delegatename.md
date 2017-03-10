---
title: "O m&#233;todo &#39;&lt; methodname &gt;&#39; n&#227;o tem uma assinatura compat&#237;vel com delegado &lt;&#39;delegatename &#39; &gt; | Microsoft Docs"
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
  - "vbc31143"
  - "bc31143"
helpviewer_keywords: 
  - "BC31143"
ms.assetid: 88990637-7c92-467e-a3d3-db5498dc1dce
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O m&#233;todo &#39;&lt; methodname &gt;&#39; n&#227;o tem uma assinatura compat&#237;vel com delegado &lt;&#39;delegatename &#39; &gt;
Esse erro ocorre quando uma conversão é exigida entre um método e um delegado que não é possível. A causa do erro pode ser conversão entre parâmetros ou, quando o método e delegado são funções, conversão de valores de retorno.  
  
 O código a seguir ilustra conversões que falharam. O representante é `FunDel`.  
  
```vb#  
Delegate Function FunDel(ByVal i As Integer, ByVal d As Double) As Integer  
```  
  
 As funções a seguir diferem das `FunDel` de forma que irá causar esse erro.  
  
```vb#  
Function ExampleMethod1(ByVal m As Integer, ByVal aDate As Date) As Integer End Function Function ExampleMethod2(ByVal m As Integer, ByVal aDouble As Double) As Date End Function  
```  
  
 Cada uma das seguintes declarações de designação causa o erro.  
  
```vb#  
Sub Main() ' The second parameters of FunDel and ExampleMethod1, Double and Date, ' are not compatible. 'Dim d1 As FunDel = AddressOf ExampleMethod1 ' The return types of FunDel and ExampleMethod2, Integer and Date, ' are not compatible. 'Dim d2 As FunDel = AddressOf ExampleMethod2 End Sub  
```  
  
 **ID do erro:** BC31143  
  
### Para corrigir este erro  
  
-   Examine os parâmetros correspondentes e, se estiverem presentes, tipos de retorno para determinar qual par não é compatível.  
  
## Consulte também  
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)