---
title: "Tipo de delegado &#39;&lt; nomedelegado &gt;&#39; de evento &#39;&lt; eventname &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
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
  - "bc40050"
  - "vbc40050"
helpviewer_keywords: 
  - "BC40050"
ms.assetid: 92f5be26-9a82-46d4-bf97-005f2c7ca424
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de delegado &#39;&lt; nomedelegado &gt;&#39; de evento &#39;&lt; eventname &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS
Um [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement) usa um representante para especificar sua assinatura, mas o [Instrução Delegate](/dotnet/visual-basic/language-reference/statements/delegate-statement) está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> atributo a um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40050  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS e tem controle sobre a definição do delegado, aplicar <xref:System.CLSCompliantAttribute> para sua declaração para marcá\-lo como `<CLSCompliant(True)>`.  
  
-   Se você não tem controle sobre a definição do representante ou não pode marcá\-la como compatível, remova o <xref:System.CLSCompliantAttribute> do `Event` instrução ou marcá\-lo como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)