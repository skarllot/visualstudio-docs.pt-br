---
title: "Vari&#225;veis locais dentro de m&#233;todos gen&#233;ricos n&#227;o podem ser declaradas &#39;Static&#39; | Microsoft Docs"
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
  - "vbc32068"
  - "bc32068"
helpviewer_keywords: 
  - "BC32068"
ms.assetid: cb5df484-76f9-4092-9d19-f26ddcf1c035
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;veis locais dentro de m&#233;todos gen&#233;ricos n&#227;o podem ser declaradas &#39;Static&#39;
Especifica a declaração de uma variável local dentro de um procedimento genérico `Static`.  
  
 Visual Basic e o .NET Framework atualmente não suportam qualquer combinação de variáveis estáticas e procedimentos genéricos.  
  
 **ID do erro:** BC32068  
  
### Para corrigir este erro  
  
-   Remover o `Static` palavra\-chave da declaração da variável.  
  
## Consulte também  
 [Estático](/dotnet/visual-basic/language-reference/modifiers/static)   
 [NOTINBUILD como: aumentar o tempo de vida da variável](http://msdn.microsoft.com/pt-br/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimentos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)