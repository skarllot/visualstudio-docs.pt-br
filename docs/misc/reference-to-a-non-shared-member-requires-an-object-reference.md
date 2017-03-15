---
title: "Refer&#234;ncia a um membro n&#227;o compartilhado requer uma refer&#234;ncia de objeto | Microsoft Docs"
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
  - "bc30469"
  - "vbc30469"
helpviewer_keywords: 
  - "BC30469"
ms.assetid: af503e8b-2e1f-4f91-a07f-b1ddd73dd4a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia a um membro n&#227;o compartilhado requer uma refer&#234;ncia de objeto
Você tem referência a um membro não compartilhado dentro de seu código e não conseguiu fornecer uma referência de objeto. Você não pode usar o nome da classe para qualificar um membro que não seja compartilhado. A instância primeiro deve ser declarado como uma variável de objeto e, em seguida, são referenciados pelo nome da variável.  
  
 **ID do erro:** BC30469  
  
### Para corrigir este erro  
  
1.  Declare a instância como uma variável de objeto.  
  
2.  Referência à instância pelo nome da variável.  
  
## Consulte também  
 [NÃO está em compilação: Noções básicas sobre Classes](http://msdn.microsoft.com/pt-br/cc2355a2-cb98-4353-9440-736585aec46c)   
 [NÃO está em compilação: Shared Members in Visual Basic](http://msdn.microsoft.com/pt-br/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NOTINBUILD: Resolvendo uma referência quando várias variáveis têm o mesmo nome](http://msdn.microsoft.com/pt-br/9601e39f-1911-44e1-ace5-3f6e090408b9)