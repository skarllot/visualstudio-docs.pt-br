---
title: "&#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque ele expande o acesso do m&#233;todo base | Microsoft Docs"
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
  - "vbc32203"
  - "bc32203"
helpviewer_keywords: 
  - "BC32203"
ms.assetid: ef7816a4-5f57-4346-80fc-9311bc150b6b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque ele expande o acesso do m&#233;todo base
Especifica um procedimento `Overrides` mas declara uma acessibilidade menos restritivo que o método seja substituído. Você não pode expandir a acessibilidade, que significa que você não pode fazer mais acessível do que o método que substitui o método de substituição. Por exemplo, se o método da classe base é `Protected`, você não pode substituí\-lo com um `Public` método.  
  
 **ID do erro:** BC32203  
  
### Para corrigir este erro  
  
-   Remover o `Overrides` palavra\-chave, ou alterar a acessibilidade para ser pelo menos tão restritivo do que o método da classe base.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Níveis de acesso no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Sombreamento no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)