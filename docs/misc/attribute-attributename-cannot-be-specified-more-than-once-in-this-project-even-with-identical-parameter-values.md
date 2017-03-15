---
title: "O atributo &#39;&lt; attributename &gt;&#39; n&#227;o pode ser especificado mais de uma vez neste projeto, mesmo com valores de par&#226;metro id&#234;nticos | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41000"
  - "vbc41000"
helpviewer_keywords: 
  - "BC41000"
ms.assetid: 7e846177-7b89-44da-8f17-cdc8606ef148
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O atributo &#39;&lt; attributename &gt;&#39; n&#227;o pode ser especificado mais de uma vez neste projeto, mesmo com valores de par&#226;metro id&#234;nticos
Um atributo personalizado está especificado mais de uma vez no mesmo elemento de programação, mas um <xref:System.AttributeUsageAttribute> é aplicada ao atributo personalizado e sua <xref:System.AttributeUsageAttribute.AllowMultiple%2A> está definida como `False`.<xref:System.AttributeUsageAttribute.AllowMultiple%2A> Controla se o atributo é multiuso.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC41000  
  
### Para corrigir este erro  
  
-   Remova a especificação extra de atributo personalizado, ou defina <xref:System.AttributeUsageAttribute.AllowMultiple%2A> para `True` no <xref:System.AttributeUsageAttribute> aplicada a ele.  
  
## Consulte também  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A>   
 [NÃO está em compilação: Aplicação de atributos](http://msdn.microsoft.com/pt-br/2b1703ed-4437-49b3-bc0b-568094324f47)