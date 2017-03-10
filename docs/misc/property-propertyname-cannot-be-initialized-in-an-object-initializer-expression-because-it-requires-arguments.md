---
title: "A propriedade &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser inicializada em uma express&#227;o de inicializador de objeto porque ela requer argumentos | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30992"
  - "vbc30992"
helpviewer_keywords: 
  - "BC30992"
ms.assetid: a4d050b2-7366-457a-a852-8eb490c97573
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A propriedade &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser inicializada em uma express&#227;o de inicializador de objeto porque ela requer argumentos
Os membros inicializados em uma lista de inicializadores de objeto devem ser campos ou propriedades, e membros de propriedade não podem ter parâmetros. Por exemplo, propriedades padrão exigem argumentos, portanto eles não podem ser inicializados em uma lista de inicializadores de objeto. Para obter mais informações, consulte [não está em compilação: propriedades padrão](http://msdn.microsoft.com/pt-br/a70f2a27-8176-4858-935e-f25afdd43ab5).  
  
 **ID do erro:** BC30992  
  
### Para corrigir este erro  
  
-   Remova da lista de inicialização todas as propriedades que possuem argumentos.  
  
## Exemplo  
 A seguinte classe contém uma propriedade padrão, `defaultProp`, que requer um argumento integer.  
  
```  
Public Class SomeStrings Private myStrings() As String Sub New(ByVal size As Integer) ReDim myStrings(size) End Sub Default Property defaultProp(ByVal index As Integer) As String Get Return myStrings(index) End Get Set(ByVal Value As String) myStrings(index) = Value End Set End Property End Class  
```  
  
 Como a propriedade padrão requer um argumento, a seguinte declaração causa um erro.  
  
```  
' Dim strs As New SomeStrings(2) With { .defaultProp = "One" }  
```  
  
## Consulte também  
 [NÃO está em compilação: Propriedades do padrão](http://msdn.microsoft.com/pt-br/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [NÃO está em compilação: Propriedades e procedimentos de propriedade](http://msdn.microsoft.com/pt-br/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)