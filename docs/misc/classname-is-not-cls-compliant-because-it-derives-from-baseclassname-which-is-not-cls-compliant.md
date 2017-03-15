---
title: "&#39;&lt; classname &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS porque deriva de &#39;&lt; baseclassname &gt;&#39;, que n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40026"
  - "bc40026"
helpviewer_keywords: 
  - "BC40026"
ms.assetid: debcd5e4-75e7-4b14-a6cc-18f1009fe52c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; classname &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS porque deriva de &#39;&lt; baseclassname &gt;&#39;, que n&#227;o &#233; compat&#237;vel com CLS
Uma classe ou interface está marcado como `<CLSCompliant(True)>` quando ela deriva de ou implementa um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para uma classe ou interface seja compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), sua hierarquia de herança inteira deve ser compatível. Isso significa que cada tipo do qual ele herda, direta ou indiretamente, deve ser compatível. Da mesma forma, se uma classe implementa uma ou mais interfaces, eles devem todos ser compatíveis em suas hierarquias de herança.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40026  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina este tipo em um esquema de implementação ou hierarquia de herança diferente.  
  
-   Se você precisar que esse tipo permaneça em seu esquema atual de implementação ou hierarquia de herança, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque\-a como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)