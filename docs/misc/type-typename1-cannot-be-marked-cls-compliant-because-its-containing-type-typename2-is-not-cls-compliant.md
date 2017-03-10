---
title: "O tipo &#39;&lt; typename1 &gt;&#39; n&#227;o pode ser marcado com CLS porque seu tipo recipiente &#39;&lt; typename2 &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
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
  - "vbc40030"
  - "bc40030"
helpviewer_keywords: 
  - "BC40030"
ms.assetid: f1cfcf04-2a99-46ef-ac87-34cc2099125c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename1 &gt;&#39; n&#227;o pode ser marcado com CLS porque seu tipo recipiente &#39;&lt; typename2 &gt;&#39; n&#227;o &#233; compat&#237;vel com CLS
Uma classe ou interface está marcado como `<CLSCompliant(True)>` quando ele está aninhado em um tipo que está marcado como `<CLSCompliant(False)>` ou não está marcado.  
  
 Para uma classe ou interface seja compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), sua hierarquia de confinamento inteira deve ser compatível. Isso significa que cada tipo no qual ele está aninhado deve ser compatível.  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, essa mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40030  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina este tipo em uma hierarquia de confinamento diferentes.  
  
-   Se você precisar que esse tipo permaneça em sua hierarquia de confinamento atual, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque\-a como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [\< PAVE OVER \> escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)