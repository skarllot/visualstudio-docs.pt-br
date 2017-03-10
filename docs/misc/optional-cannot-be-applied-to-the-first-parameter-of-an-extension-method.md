---
title: "&#39;Optional&#39; n&#227;o pode ser aplicado ao primeiro par&#226;metro de um m&#233;todo de extens&#227;o | Microsoft Docs"
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
  - "bc36553"
  - "vbc36553"
helpviewer_keywords: 
  - "BC36553"
ms.assetid: 8ea0b90c-f155-47a9-988b-5b8009b510af
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Optional&#39; n&#227;o pode ser aplicado ao primeiro par&#226;metro de um m&#233;todo de extens&#227;o
'Optional' não pode ser aplicado ao primeiro parâmetro de um método de extensão. O primeiro parâmetro especifica que tipo para estender.  
  
 O primeiro parâmetro de um método de extensão especifica o tipo de dados que o método estende. Quando o método for executado, o primeiro parâmetro é associado à instância do tipo de dados que chama o método. Portanto, o primeiro parâmetro é obrigatório e não pode ser opcional.  
  
 A restrição se aplica somente ao primeiro parâmetro. Outros parâmetros podem ser opcionais ou não, seguindo as mesmas regras de qualquer outro método. Para obter mais informações, consulte [Lista de parâmetros](/dotnet/visual-basic/language-reference/statements/parameter-list).  
  
 **ID do erro:** BC36553  
  
### Para corrigir este erro  
  
-   Se você quiser que o primeiro parâmetro para especificar o tipo de dados que está sendo estendido, remova a atual o `Optional` palavra\-chave.  
  
-   Se o primeiro parâmetro atual é um parâmetro para o método padrão e não quiser que representam o tipo de dados que está sendo estendido, adicione um novo primeiro parâmetro.  
  
## Exemplo  
 O primeiro parâmetro no exemplo a seguir é a única indicação de que o `Print` método estende o `String` tipo de dados. Portanto, não pode ser opcional.  
  
```  
<Extension()> Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 Quando o método de extensão é chamado como segue, parâmetro `str` no método é associado a `greeting`, a instância de `String` que chama `Print`. O compilador usa `greeting` como o argumento para o método de extensão `Print`.  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Como: definir parâmetros opcionais para um procedimento \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0b32b312-0da0-489b-96ad-7dcb1f1f8f88)   
 [Parâmetros opcionais](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)