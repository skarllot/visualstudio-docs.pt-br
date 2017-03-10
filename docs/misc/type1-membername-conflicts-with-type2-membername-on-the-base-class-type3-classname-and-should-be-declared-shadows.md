---
title: "&lt; type1 &gt; &#39;&lt; nome do membro &gt;&#39; est&#225; em conflito com &lt; type2 &gt; &#39;&lt; nome do membro &gt;&#39; na classe base &lt; Tipo3 &gt; &#39;&lt; classname &gt;&#39; e deve ser declarado como &#39;Shadows&#39; | Microsoft Docs"
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
  - "bc40004"
  - "vbc40004"
helpviewer_keywords: 
  - "BC40004"
ms.assetid: 24d10f31-3b3d-448c-b928-fc937e1f4a92
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; type1 &gt; &#39;&lt; nome do membro &gt;&#39; est&#225; em conflito com &lt; type2 &gt; &#39;&lt; nome do membro &gt;&#39; na classe base &lt; Tipo3 &gt; &#39;&lt; classname &gt;&#39; e deve ser declarado como &#39;Shadows&#39;
Um elemento de programação é declarado com o mesmo nome que um elemento definido na classe base. Nessa situação, o elemento nessa classe deve sombrear o elemento da classe base.  
  
 Essa mensagem é um aviso.`Shadows` será considerado por padrão. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID do erro:** BC40004  
  
### Para corrigir este erro  
  
-   Adicionar o `Shadows` palavra\-chave para a declaração, ou alterar o nome do elemento que está sendo declarado.  
  
## Consulte também  
 [Sombras](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Sombreamento no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)