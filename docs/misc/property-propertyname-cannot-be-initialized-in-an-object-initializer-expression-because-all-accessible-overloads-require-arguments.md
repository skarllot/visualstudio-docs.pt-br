---
title: "A propriedade &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser inicializada em uma express&#227;o de inicializador de objeto porque todas as sobrecargas acess&#237;veis requerem argumentos | Microsoft Docs"
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
  - "bc30993"
  - "vbc30993"
helpviewer_keywords: 
  - "BC30993"
ms.assetid: d4476065-2ca2-4c9e-a571-c08917a6387f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A propriedade &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser inicializada em uma express&#227;o de inicializador de objeto porque todas as sobrecargas acess&#237;veis requerem argumentos
Os membros inicializados em uma lista de inicializadores de objeto devem ser campos ou propriedades. Além disso, propriedades em uma lista de inicializadores não podem ter parâmetros. A propriedade causando o erro está sobrecarregada, e cada uma das suas versões requer argumentos. Portanto, a propriedade não pode ser inicializada em uma lista de inicializadores de objeto.  
  
 **ID do erro:** BC30993  
  
### Para corrigir este erro  
  
-   Remova a propriedade que requer argumentos da lista do inicializador.  
  
## Exemplo  
 A seguinte classe contém três definições de propriedade: uma para `TotalItems` e dois para `Item`, que está sobrecarregado.  
  
```  
Class CollectionOfItems Property TotalItems() As Integer Get End Get Set(ByVal value As Integer) End Set End Property Property Item(ByVal Key As String) As Object Get End Get Set(ByVal value As Object) End Set End Property Property Item(ByVal Index As Integer) As Object Get End Get Set(ByVal value As Object) End Set End Property End Class  
```  
  
 O `TotalItems` propriedade não requer nenhum argumento e pode ser inicializada em uma lista de inicialização de objeto, conforme mostrado na seguinte declaração.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 }  
```  
  
 O `Item` propriedade está sobrecarregada, e cada sobrecarga exige um argumento. Portanto, `Item` não pode aparecer em uma lista de inicializadores de objeto.  
  
```  
' The following declaration is not valid. ' Dim coinCollection As New CollectionOfItems With { .TotalItems = 0, _ '    .Item = aCoinObject }  
```  
  
 Para evitar esse erro, inicialize o `Item` propriedade fora do inicializador de objeto.  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 } coinCollection.Item(1) = aCoinObject  
```  
  
## Consulte também  
 [NÃO está em compilação: Propriedades e procedimentos de propriedade](http://msdn.microsoft.com/pt-br/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Como chamar um procedimento de propriedade](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [NÃO está em compilação: Propriedades do padrão](http://msdn.microsoft.com/pt-br/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)