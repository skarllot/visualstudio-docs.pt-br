---
title: "Nome do par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; n&#227;o coincide com o nome &#39;&lt; typeparametername2 &gt;&#39; do par&#226;metro de tipo correspondente definido em um dos outros tipos parciais de &#39;&lt; partialtypename &gt;&#39; | Microsoft Docs"
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
  - "vbc30931"
  - "bc30931"
helpviewer_keywords: 
  - "BC30931"
ms.assetid: 01b053c3-d1b5-4e69-b908-3d5cfc73913b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nome do par&#226;metro de tipo &#39;&lt; typeparametername1 &gt;&#39; n&#227;o coincide com o nome &#39;&lt; typeparametername2 &gt;&#39; do par&#226;metro de tipo correspondente definido em um dos outros tipos parciais de &#39;&lt; partialtypename &gt;&#39;
Uma classe ou estrutura genérica é definida em várias declarações parciais com especificações de parâmetro do tipo conflitantes.  
  
 Quando você divide a definição de uma classe ou estrutura entre várias declarações parciais, o compilador trata o tipo como a união de todas as suas declarações parciais. Isso se aplica não apenas aos membros mas também para a implementação, herança e nível de acesso.  
  
 Você não pode especificar vários nomes para qualquer parâmetro de tipo na definição de uma classe genérica ou estrutura.  
  
 **ID do erro:** BC30931  
  
### Para corrigir este erro  
  
-   Decida qual nome o parâmetro de tipo deve ter e use o mesmo nome em cada declaração parcial.  
  
## Consulte também  
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Instrução Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [NÃO está em compilação: Classes: desenhos para objetos](http://msdn.microsoft.com/pt-br/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Estruturas](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)