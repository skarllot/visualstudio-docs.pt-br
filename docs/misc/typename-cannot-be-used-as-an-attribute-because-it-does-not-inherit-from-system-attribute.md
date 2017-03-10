---
title: "&#39;&lt; typename &gt;&#39; n&#227;o pode ser usado como um atributo porque ele n&#227;o herda de &#39;System. Attribute&#39; | Microsoft Docs"
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
  - "vbc31504"
  - "bc31504"
helpviewer_keywords: 
  - "BC31504"
ms.assetid: 37517623-5099-4db9-a461-f2f5daa4957b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; typename &gt;&#39; n&#227;o pode ser usado como um atributo porque ele n&#227;o herda de &#39;System. Attribute&#39;
Foi feita uma tentativa para usar uma classe que não é derivada de `System.Attribute`.  
  
 **ID do erro:** BC31504  
  
### Para corrigir este erro  
  
1.  Defina atributos personalizados como classes que derivam de `System.Attribute` Adicionando um `Imports` instrução para a primeira linha do código na classe.  
  
## Consulte também  
 <xref:System.AttributeUsageAttribute>   
 [NÃO está em compilação: Atributos personalizados no Visual Basic](http://msdn.microsoft.com/pt-br/d72d8a5c-8f64-4614-b15b-cad66845d047)