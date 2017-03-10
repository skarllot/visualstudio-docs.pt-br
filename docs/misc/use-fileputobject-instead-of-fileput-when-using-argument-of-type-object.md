---
title: "Use &#39;FilePutObject&#39; em vez de &#39;FilePut&#39; quando usar argumento do tipo &#39;Object&#39; | Microsoft Docs"
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
  - "vbrUseFilePutObject"
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Use &#39;FilePutObject&#39; em vez de &#39;FilePut&#39; quando usar argumento do tipo &#39;Object&#39;
O `FilePut` método inclui um argumento do tipo`Object`.`FilePutObject` deve ser usado no lugar de `FilePut` para evitar ambiguidades.  
  
### Para corrigir este erro  
  
-   Substitua `FilePut` com `FilePutObject`.  
  
-   Conversão de `Object` argumento para um tipo mais específico.  
  
-   Use a funcionalidade disponível no `My.Computer.FileSystem` objeto.  
  
## Consulte também  
 [NÃO está em compilação: Função FilePutObject](http://msdn.microsoft.com/pt-br/a0f52a1c-5ecc-4945-b18c-03147af61d6b)   
 [Objeto My.Computer.FileSystem](/dotnet/visual-basic/language-reference/objects/my-computer-filesystem-object)   
 [Método WriteAllBytes](http://msdn.microsoft.com/pt-br/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)