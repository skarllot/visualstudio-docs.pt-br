---
title: "O acesso especificado &#39;&lt; accesslevel1 &gt;&#39; para &#39;&lt; partialtypename &gt;&#39; n&#227;o corresponde ao acesso &#39;&lt; accesslevel2 &gt;&#39; especificado em um de seus outros tipos parciais | Microsoft Docs"
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
  - "vbc30925"
  - "BC30925"
helpviewer_keywords: 
  - "BC30925"
ms.assetid: aabe0f4a-dc02-4828-a837-20cd47a7bd43
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O acesso especificado &#39;&lt; accesslevel1 &gt;&#39; para &#39;&lt; partialtypename &gt;&#39; n&#227;o corresponde ao acesso &#39;&lt; accesslevel2 &gt;&#39; especificado em um de seus outros tipos parciais
Uma classe ou estrutura é definida em várias declarações parciais com especificações de nível de acesso conflitantes.  
  
 Quando você divide a definição de uma classe ou estrutura entre várias declarações parciais, o compilador trata o tipo como a união de todas as suas declarações parciais. Isso se aplica não apenas aos membros mas também para a implementação, herança e nível de acesso.  
  
 Você não pode misturar níveis de acesso na definição de uma classe ou estrutura. Até mesmo a combinação `Protected Friend` é permitida apenas quando as palavras\-chave são contíguas na mesma instrução de declaração.  
  
 **ID do erro:** BC30925  
  
### Para corrigir este erro  
  
-   Decidir qual deve ser o nível de acesso da classe e remove quaisquer especificações de nível de acesso conflitantes.  
  
## Consulte também  
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Níveis de acesso no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Instrução Class](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Instrução Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [NÃO está em compilação: Classes: desenhos para objetos](http://msdn.microsoft.com/pt-br/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Estruturas](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)