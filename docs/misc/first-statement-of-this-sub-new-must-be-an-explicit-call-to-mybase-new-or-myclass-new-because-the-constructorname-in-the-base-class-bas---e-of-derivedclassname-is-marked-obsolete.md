---
title: "A primeira instru&#231;&#227;o deste &#39;Sub New&#39; deve ser uma chamada expl&#237;cita para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; porque o &#39;&lt; constructorname &gt;&#39; na classe base &#39;&lt; baseclassname &gt;&#39; de &#39;&lt; derivedclassname &gt;&#39; est&#225; marcado como obsoleto. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30919"
  - "bc30919"
helpviewer_keywords: 
  - "BC30919"
ms.assetid: 437e3204-8ddc-45d3-b9b4-c66d53a61a6d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A primeira instru&#231;&#227;o deste &#39;Sub New&#39; deve ser uma chamada expl&#237;cita para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; porque o &#39;&lt; constructorname &gt;&#39; na classe base &#39;&lt; baseclassname &gt;&#39; de &#39;&lt; derivedclassname &gt;&#39; est&#225; marcado como obsoleto.
Um construtor de classe não chama explicitamente um construtor de classe base, e o construtor de classe de base implícito está marcado com o <xref:System.ObsoleteAttribute> atributo e com a diretriz para tratá\-lo como um erro.  
  
 Quando um construtor de classe derivada não chama um construtor de classe base, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tenta gerar uma chamada implícita para um construtor de classe base sem parâmetros. Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não é possível gerar uma chamada implícita. Nesse caso, o construtor exigido é marcado com o <xref:System.ObsoleteAttribute> atributo, isso [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não pode chamá\-lo.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`. Se você defini\-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini\-lo como `False`, ou deixá\-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 **ID do erro:** BC30919  
  
### Para corrigir este erro  
  
-   Incluir uma chamada para `MyBase.New()` ou `MyClass.New()` como a primeira instrução do `Sub New` na classe derivada.  
  
## Consulte também  
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)