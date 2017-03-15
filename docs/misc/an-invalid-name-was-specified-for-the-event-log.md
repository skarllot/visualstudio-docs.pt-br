---
title: "Um nome inv&#225;lido foi especificado para o log de eventos | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Um nome inv&#225;lido foi especificado para o log de eventos
Um nome inválido foi especificado para o log de eventos. Geralmente, isso é resultado dos caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo é muito longo.  
  
### Para corrigir este erro  
  
-   Se o nome especificado é mais de oito caracteres, verifique se que não há nenhum conflito com os nomes dos outros logs de eventos. Somente os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.  
  
-   Se fornecer um caminho, verifique se que ele é analisado corretamente.  
  
-   Verificar não se há nenhum caractere inválido no nome. Caracteres que não podem ser usados em um nome de arquivo incluem `<`, `>`, `:`, `"`, `/`, `\`, e `|`.  
  
## Consulte também  
 [Como analisar caminhos de arquivo](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)   
 [Como renomear um arquivo](../Topic/How%20to:%20Rename%20a%20File%20in%20Visual%20Basic.md)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/pt-br/af9b7da0-80c7-46ac-b7f7-897063ddd503)