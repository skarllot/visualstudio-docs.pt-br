---
title: "Classe &#39;&lt; classname &gt;&#39; deve declarar um &#39;Sub New&#39; porque o &#39;&lt; constructorname &gt;&#39; na sua classe base &#39;&lt; baseclassname &gt;&#39; est&#225; marcado como obsoleto | Microsoft Docs"
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
  - "bc41001"
  - "vbc41001"
helpviewer_keywords: 
  - "BC41001"
ms.assetid: b2c6b996-6d52-4963-9fee-8b6f78fc028c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classe &#39;&lt; classname &gt;&#39; deve declarar um &#39;Sub New&#39; porque o &#39;&lt; constructorname &gt;&#39; na sua classe base &#39;&lt; baseclassname &gt;&#39; est&#225; marcado como obsoleto
Uma declaração de classe não inclui um construtor, e o construtor da classe base é marcado com o <xref:System.ObsoleteAttribute> atributo e com a diretriz para tratá\-lo como um aviso.  
  
 Quando uma classe derivada não declara um construtor, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tenta gerar um construtor implícito sem parâmetros que chama `MyBase.New()`. Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não é possível gerar um construtor implícito. Nesse caso, o construtor exigido é marcado com o <xref:System.ObsoleteAttribute> atributo, isso [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não pode chamá\-lo.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`. Se você defini\-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini\-lo como `False`, ou deixá\-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 Por padrão, essa mensagem é um aviso, porque o <xref:System.ObsoleteAttribute.IsError%2A> propriedade <xref:System.ObsoleteAttribute> é `False`. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC41001  
  
### Para corrigir este erro  
  
1.  Use `Sub New` para declarar um construtor na classe derivada.  
  
## Consulte também  
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)