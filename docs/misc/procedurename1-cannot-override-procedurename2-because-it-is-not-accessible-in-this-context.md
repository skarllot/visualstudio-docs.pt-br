---
title: "&#39;&lt; procedurename1 &gt;&#39; n&#227;o pode substituir &#39;&lt; procedurename2 &gt;&#39; porque ele n&#227;o est&#225; acess&#237;vel neste contexto | Microsoft Docs"
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
  - "bc31417"
  - "vbc31417"
helpviewer_keywords: 
  - "BC31417"
ms.assetid: 1a36acbf-cead-43a0-b12f-f52f94d09124
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; procedurename1 &gt;&#39; n&#227;o pode substituir &#39;&lt; procedurename2 &gt;&#39; porque ele n&#227;o est&#225; acess&#237;vel neste contexto
Um procedimento ou uma propriedade substitui um procedimento ou uma propriedade com um nível de acesso que impede o acesso pelo procedimento ou propriedade de substituição.  
  
 Por exemplo, se um procedimento é declarado como `Friend` em um assembly, ele não pode ser acessado fora desse assembly. Se um procedimento em outro assembly no mesmo projeto tenta substituir o `Friend` procedimento, ele não pode acessá\-lo para substituí\-lo.  
  
 **ID do erro:** BC31417  
  
### Para corrigir este erro  
  
-   Mova a propriedade ou procedimento de substituição para o mesmo assembly que o procedimento ou propriedade deve substituir.  
  
     \- ou \-  
  
-   Remover o `Overrides` palavra\-chave.  
  
## Consulte também  
 [Níveis de acesso no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Substituições](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)