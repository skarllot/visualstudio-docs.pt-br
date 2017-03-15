---
title: "Construtor de atributo tem um par&#226;metro do tipo &#39;&lt; type &gt;&#39;, que n&#227;o &#233; inteiro, ponto flutuante ou tipo Enum ou um Char, String, Boolean, System. Type ou matriz em 1 dimens&#227;o desses tipos de | Microsoft Docs"
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
  - "bc30045"
  - "vbc30045"
helpviewer_keywords: 
  - "BC30045"
ms.assetid: 16899755-7901-4c56-ae90-54c3532e8319
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Construtor de atributo tem um par&#226;metro do tipo &#39;&lt; type &gt;&#39;, que n&#227;o &#233; inteiro, ponto flutuante ou tipo Enum ou um Char, String, Boolean, System. Type ou matriz em 1 dimens&#227;o desses tipos de
Uma definição de atributo personalizado inclui um construtor que especifica um tipo de dados inválido para um parâmetro. Atributos podem levar apenas certos tipos de dados como parâmetros, porque apenas esses tipos podem ser serializados para os metadados do assembly.  
  
 **ID do erro:** BC30045  
  
### Para corrigir este erro  
  
1.  Altere o tipo de dados do parâmetro para `Byte`, `Short`, `Integer`, `Long`, `Single`, `Double`, `Char`, `String`, `Boolean`, `System.Type`, ou um tipo de enumeração.  
  
## Consulte também  
 [NÃO está em compilação: Atributos personalizados no Visual Basic](http://msdn.microsoft.com/pt-br/d72d8a5c-8f64-4614-b15b-cad66845d047)