---
title: "O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; s&#243; pode ter uma restri&#231;&#227;o que &#233; uma classe | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32047"
  - "vbc32047"
helpviewer_keywords: 
  - "BC32047"
ms.assetid: ac7ab76b-5300-4c79-b519-5a1287ed5fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro de tipo &#39;&lt; typeparametername &gt;&#39; s&#243; pode ter uma restri&#231;&#227;o que &#233; uma classe
Uma lista de restrição inclui mais de uma classe.  
  
 Uma lista de restrição em um parâmetro de tipo pode aceitar qualquer número de interfaces, mas no máximo uma classe. Um argumento de tipo fornecido para esse parâmetro de tipo deve herdar da classe, e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não oferece suporte a várias heranças.  
  
 **ID do erro:** BC32047  
  
### Para corrigir este erro  
  
-   Selecione uma classe e inclua somente essa classe na lista de restrição.  
  
-   É possível definir os parâmetros de tipo adicionais para acomodar a classe ou classes que você não pode incluir na lista restrição.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)