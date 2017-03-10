---
title: "&lt; type1 &gt; &#39;&lt; typename &gt;&#39; n&#227;o pode ser declarado como &#39;Overrides&#39; porque n&#227;o substitui um &lt; type1 &gt; em uma base de &lt; type2 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30284"
  - "bc30284"
helpviewer_keywords: 
  - "BC30284"
ms.assetid: 8166bd09-dad3-495d-8cf7-66f90824a288
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; type1 &gt; &#39;&lt; typename &gt;&#39; n&#227;o pode ser declarado como &#39;Overrides&#39; porque n&#227;o substitui um &lt; type1 &gt; em uma base de &lt; type2 &gt;
Um `Sub`, `Function`, ou `Property` declaração especifica `Overrides` quando nenhum tipo com o mesmo nome existe na classe base.  
  
 **ID do erro:** BC30284  
  
### Para corrigir este erro  
  
1.  Verifique se o nome do tipo está escrito corretamente.  
  
2.  Remover o supérfluo `Overrides` palavra\-chave.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)