---
title: "Propriedade de atributo &#39;Shared&#39; &#39;&lt; propertyfield &gt;&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o | Microsoft Docs"
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
  - "bc31500"
  - "vbc31500"
helpviewer_keywords: 
  - "BC31500"
ms.assetid: dffa2b07-9609-4aa3-ae58-c0804d8a05d6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade de atributo &#39;Shared&#39; &#39;&lt; propertyfield &gt;&#39; n&#227;o pode ser o destino de uma atribui&#231;&#227;o
Foi feita uma tentativa para atribuir um valor para um `ReadOnly` ou `Shared` propriedade em um atributo.  
  
 **ID do erro:** BC31500  
  
### Para corrigir este erro  
  
1.  Remova a instrução de atribuição de propriedade.  
  
2.  Se usando propriedades você desenvolveu, remova o `ReadOnly` ou `Shared` modificadores da propriedade de atributo.  
  
## Consulte também  
 [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)