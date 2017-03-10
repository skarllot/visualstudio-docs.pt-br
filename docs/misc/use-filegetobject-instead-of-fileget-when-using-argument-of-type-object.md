---
title: "Use &#39;FileGetObject&#39; em vez de &#39;FileGet&#39; quando usar argumento do tipo &#39;Object&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Use &#39;FileGetObject&#39; em vez de &#39;FileGet&#39; quando usar argumento do tipo &#39;Object&#39;
O `FileGet` método inclui um argumento do tipo `Object`.`FileGetObject` deve ser usado no lugar de `FileGet` para evitar ambiguidades.  
  
 Observe que a funcionalidade oferecida pelo `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que o `FileGet` ou `FileGetObject`.  
  
### Para corrigir este erro  
  
1.  Substitua `FileGet` com `FileGetObject`.  
  
2.  Conversão de `Object` argumento para um tipo mais específico.  
  
## Consulte também  
 [NÃO está em compilação: Função FileGetObject](http://msdn.microsoft.com/pt-br/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)   
 [Objeto My.Computer.FileSystem](/dotnet/visual-basic/language-reference/objects/my-computer-filesystem-object)