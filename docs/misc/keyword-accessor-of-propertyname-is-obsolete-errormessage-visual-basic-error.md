---
title: "acessador &#39;&lt; palavra-chave &gt;&#39; de &#39;&lt; propertyname &gt;&#39; est&#225; obsoleto: &#39;&lt; errormessage &gt;&#39; (erro do Visual Basic) | Microsoft Docs"
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
  - "vbc30911"
  - "bc30911"
helpviewer_keywords: 
  - "BC30911"
ms.assetid: b690be0c-4dca-4f79-88ed-4ee3e3f1f90b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# acessador &#39;&lt; palavra-chave &gt;&#39; de &#39;&lt; propertyname &gt;&#39; est&#225; obsoleto: &#39;&lt; errormessage &gt;&#39; (erro do Visual Basic)
Uma declaração tenta ler ou gravar uma propriedade para o qual o procedimento correspondente foi marcado com o <xref:System.ObsoleteAttribute> atributo e com a diretriz para tratá\-lo como um erro.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`. Se você defini\-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini\-lo como `False`, ou deixá\-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 **ID do erro:** BC30911  
  
### Para corrigir este erro  
  
1.  Examine a mensagem de erro entre aspas e tomar as devidas providências.  
  
2.  Certifique\-se de que a referência do código\-fonte é o nome da propriedade digitado corretamente.  
  
3.  Evite acessar a propriedade da forma \(leitura ou gravação\) que gerou essa mensagem.  
  
## Consulte também  
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)