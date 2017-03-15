---
title: "&#39;New&#39; n&#227;o pode ser usado em uma classe que &#233; declarada &#39;MustInherit&#39; | Microsoft Docs"
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
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; n&#227;o pode ser usado em uma classe que &#233; declarada &#39;MustInherit&#39;
Um `MustInherit` classe não pode ser instanciada diretamente e, portanto, o `New` operador não pode ser usado em um `MustInherit` classe. Embora seja possível ter variáveis e valores cujos tipos de tempo de compilação sejam `MustInherit`, tais variáveis e valores serão necessariamente ser um valor nulo ou conterão referências às instâncias de classes regulares derivadas da `MustInherit` tipos.  
  
 **ID do erro:** BC30569  
  
### Para corrigir este erro  
  
-   Remover o `New` operador.  
  
## Consulte também  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)