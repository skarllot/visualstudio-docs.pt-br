---
title: "Tipo &#39;&lt; typename &gt;&#39; n&#227;o pode implementar a interface &#39;&lt; interfacename &gt;&#39; porque ele declara &#39;&lt; eventsignature &gt;&#39; que tem um tipo de retorno | Microsoft Docs"
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
  - "bc30945"
  - "vbc30945"
helpviewer_keywords: 
  - "BC30945"
ms.assetid: 4f26e71a-949d-4103-b565-35cc8e833d29
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo &#39;&lt; typename &gt;&#39; n&#227;o pode implementar a interface &#39;&lt; interfacename &gt;&#39; porque ele declara &#39;&lt; eventsignature &gt;&#39; que tem um tipo de retorno
Uma classe ou estrutura tenta implementar uma interface que declara um evento que retorna um valor.  
  
 Visual Basic não oferece suporte atualmente declarando eventos que retornam valores.  
  
 **ID do erro:** BC30945  
  
### Para corrigir este erro  
  
-   Remover o `Implements` declaração da classe ou definição de estrutura ou implemente uma interface diferente.  
  
## Consulte também  
 [NÃO nos manipuladores de eventos e eventos de compilação:](http://msdn.microsoft.com/pt-br/95074a0d-1cbc-4221-a95a-964185c7f962)   
 [Instrução Implements](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NÃO está em compilação: Palavra\-chave Implements e a instrução Implements](http://msdn.microsoft.com/pt-br/b96560f7-6413-480f-a1e2-f80253bab5be)