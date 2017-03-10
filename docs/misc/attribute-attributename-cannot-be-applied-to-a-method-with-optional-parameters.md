---
title: "O atributo &#39;&lt; attributename &gt;&#39; n&#227;o pode ser aplicado a um m&#233;todo com par&#226;metros opcionais | Microsoft Docs"
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
  - "vbc30645"
  - "bc30645"
helpviewer_keywords: 
  - "BC30645"
ms.assetid: 4de3d2c9-5588-47c2-a6b2-e165d16106b8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O atributo &#39;&lt; attributename &gt;&#39; n&#227;o pode ser aplicado a um m&#233;todo com par&#226;metros opcionais
O atributo só pode ser usado com métodos que usam argumentos necessários ou nenhum argumento.  
  
 **ID do erro:** BC30645  
  
### Para corrigir este erro  
  
1.  Defina o método sem parâmetros opcionais.  
  
2.  Use um atributo que pode ser usado com métodos que têm parâmetros opcionais.  
  
3.  Defina um atributo personalizado que pode ser usado neste contexto.  
  
## Consulte também  
 <xref:System.AttributeUsageAttribute>   
 [NÃO está em compilação: Atributos no Visual Basic](http://msdn.microsoft.com/pt-br/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)