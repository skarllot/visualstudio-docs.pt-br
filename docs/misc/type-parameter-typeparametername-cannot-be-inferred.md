---
title: "O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; n&#227;o pode ser inferido. | Microsoft Docs"
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
  - "bc36572"
  - "vbc36572"
helpviewer_keywords: 
  - "BC36572"
ms.assetid: 02264070-b055-4ab0-8d2a-eac4d90d9fdf
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; n&#227;o pode ser inferido.
Um procedimento genérico é chamado sem fornecer uma lista de argumentos de tipo e Inferência de tipos falha para um dos argumentos de tipo.  
  
 Quando você chama um procedimento genérico, você normalmente fornece um argumento de tipo para cada parâmetro de tipo definido pelo procedimento. No entanto, você tem a alternativa de omitir a lista de argumentos de tipo completamente. Quando você fizer isso, o compilador tenta inferir o tipo de cada argumento de tipo do contexto de sua chamada. Para obter mais informações, consulte "Inferência de tipo" em [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures).  
  
 **ID do erro:** BC36572  
  
### Para corrigir este erro  
  
-   Verifique se que os tipos dos argumentos normais são tais que a inferência de tipos é consistente com os parâmetros de tipo declarados para o procedimento genérico.  
  
     \- ou \-  
  
-   Chame o procedimento genérico com uma lista de argumentos de tipo completo, para que a inferência de tipo não é necessária.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)