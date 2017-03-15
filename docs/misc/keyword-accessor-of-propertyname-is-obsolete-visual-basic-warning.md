---
title: "o acessador &#39;&lt; palavra-chave &gt;&#39; de &#39;&lt; propertyname &gt;&#39; est&#225; obsoleto (aviso do Visual Basic) | Microsoft Docs"
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
  - "vbc40020"
  - "bc40020"
helpviewer_keywords: 
  - "BC40020"
ms.assetid: 005440f4-6e82-421c-b2ce-9c5139325bac
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# o acessador &#39;&lt; palavra-chave &gt;&#39; de &#39;&lt; propertyname &gt;&#39; est&#225; obsoleto (aviso do Visual Basic)
Uma declaração tenta ler ou gravar uma propriedade para o qual o procedimento correspondente foi marcado com o <xref:System.ObsoleteAttribute> atributo e com a diretriz para tratá\-lo como um aviso.  
  
 Você pode marcar qualquer elemento de programação como sendo não mais em uso aplicando <xref:System.ObsoleteAttribute> a ele. Se você fizer isso, você pode definir o atributo <xref:System.ObsoleteAttribute.IsError%2A> propriedade como `True` ou `False`. Se você defini\-lo como `True`, o compilador trata uma tentativa de usar o elemento como um erro. Se você defini\-lo como `False`, ou deixá\-lo como padrão `False`, o compilador emite um aviso se houver uma tentativa de usar o elemento.  
  
 Por padrão, essa mensagem é um aviso, porque o <xref:System.ObsoleteAttribute.IsError%2A> propriedade <xref:System.ObsoleteAttribute> é `False`. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40020  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que a referência do código\-fonte é o nome da propriedade digitado corretamente.  
  
2.  Evite acessar a propriedade da forma \(leitura ou gravação\) que gerou essa mensagem.  
  
## Consulte também  
 [NÃO está em compilação: Atributos usados no Visual Basic](http://msdn.microsoft.com/pt-br/22231318-8a40-49af-9245-e0aab723563b)   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)