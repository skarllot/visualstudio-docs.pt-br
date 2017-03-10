---
title: "Membro &#39;&lt; nome do membro &gt;&#39; n&#227;o pode ser inicializado em uma express&#227;o de inicializador de objeto porque ele &#233; compartilhado | Microsoft Docs"
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
  - "bc30991"
  - "vbc30991"
helpviewer_keywords: 
  - "BC30991"
ms.assetid: 47e832b4-47e3-426e-b88c-5d5568102fde
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membro &#39;&lt; nome do membro &gt;&#39; n&#227;o pode ser inicializado em uma express&#227;o de inicializador de objeto porque ele &#233; compartilhado
Inicializadores de objeto não podem ser usados para inicializar qualquer membro de uma classe é declarada como compartilhada. Para obter mais informações, consulte [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared).  
  
 **ID do erro:** BC30991  
  
### Para corrigir este erro  
  
1.  Examine a definição de classe para determinar qual membro é compartilhado.  
  
2.  Elimine a inicialização para esse membro da lista de inicializador de objeto.  
  
## Exemplo  
 No exemplo a seguir, `totalCustomers` é um membro compartilhado.  
  
```  
Public Class Customer Public Shared totalCustomers As Integer ' Other declarations and method definitions. End Class  
```  
  
 Porque `totalCustomers` é compartilhado, tentar definir seu valor inicial em uma lista do inicializador de objeto causa esse erro.  
  
```  
' This declaration is not valid. ' Dim cust As New Customer With { .Name = "Coho Winery", _ '                                 .totalCustomers = 21 }  
```  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NÃO está em compilação: Shared Members in Visual Basic](http://msdn.microsoft.com/pt-br/dbc3783f-83a2-4225-995d-c2d6d025663d)