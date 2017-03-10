---
title: "O coment&#225;rio XML tem uma marca com um atributo &#39;cref&#39; &#39;&lt; attribute &gt;&#39; n&#227;o p&#244;de ser resolvido | Microsoft Docs"
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
  - "bc42309"
  - "vbc42309"
helpviewer_keywords: 
  - "BC42309"
ms.assetid: c9f3cfa5-565f-48bf-8616-cfb25d24f89e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O coment&#225;rio XML tem uma marca com um atributo &#39;cref&#39; &#39;&lt; attribute &gt;&#39; n&#227;o p&#244;de ser resolvido
O comentário XML tem uma marca com um atributo 'cref' \< atributo \> não pôde ser resolvido. O comentário XML será ignorado.  
  
 As marcas podem ter um `cref` atributo que designa um link para outro elemento do XML, especificando o nome do identificador relativo. Em tempo de compilação, o compilador substitui o valor com o identificador XML qualificado para o valor apontado pelo usuário. O compilador usa suas regras de resolução normal para localizar o tipo ou membro.  
  
 **ID do erro:** BC42309  
  
### Para corrigir este erro  
  
-   Validar o `cref` atributo para que ele aponta para um elemento de código válida.  
  
## Consulte também  
 [Como criar documentação XML](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [Marcas de comentário XML](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)