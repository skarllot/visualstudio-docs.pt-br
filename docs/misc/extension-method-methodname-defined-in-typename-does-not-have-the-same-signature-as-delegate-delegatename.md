---
title: "M&#233;todo de extens&#227;o &#39;&lt; methodName &gt;&#39; definido em &#39;&lt; typeName &gt;&#39; n&#227;o tem a mesma assinatura do delegado &#39;&lt; nomedelegado &gt;&#39; | Microsoft Docs"
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
  - "bc36580"
  - "vbc36580"
helpviewer_keywords: 
  - "BC36580"
ms.assetid: dc6b6a63-02b0-43d8-b6a7-c1cd397c6ee3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todo de extens&#227;o &#39;&lt; methodName &gt;&#39; definido em &#39;&lt; typeName &gt;&#39; n&#227;o tem a mesma assinatura do delegado &#39;&lt; nomedelegado &gt;&#39;
Há uma incompatibilidade entre as assinaturas do método de extensão e o delegado que você está tentando usar. O `Delegate` instrução define os tipos de parâmetro e tipos de retorno de uma classe de delegado. Qualquer procedimento com parâmetros, tipos e tipos de retorno correspondentes pode ser usado para criar uma instância do tipo delegado. Esse erro é relatado no exemplo a seguir, porque a assinatura do método de extensão `Example` não é compatível com a assinatura do delegado `Del`.  
  
```vb#  
' Definition of the delegate, with two parameters. Delegate Sub Del(ByVal m As Integer, ByVal s As String)  
```  
  
```vb#  
' Definition of the extension method, with one parameter. <Extension()> _ Sub Example(ByVal s As String) ' Body of the Sub. End Sub  
```  
  
```vb#  
'' This assignment causes the error. ' Dim exampleDel As Del = AddressOf Example  
```  
  
 **ID do erro:** BC36580  
  
### Para corrigir este erro  
  
-   Verificar se o representante e o método de extensão têm o mesmo número de parâmetros.  
  
-   Verifique se a ordem dos parâmetros é a mesma no representante e o método de extensão.  
  
-   Compare o tipo de dados de cada parâmetro delegado para o tipo de dados do parâmetro de método de extensão correspondente para certificar\-se de que eles sejam compatíveis.  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)