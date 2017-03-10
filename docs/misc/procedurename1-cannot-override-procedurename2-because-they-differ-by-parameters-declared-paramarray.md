---
title: "&lt; procedurename1 &gt; n&#227;o &#233; poss&#237;vel substituir &lt; procedurename2 &gt; porque diferem nos par&#226;metros declarados como &#39;ParamArray&#39; | Microsoft Docs"
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
  - "bc30906"
  - "vbc30906"
helpviewer_keywords: 
  - "BC30906"
ms.assetid: 12939030-732e-4c6d-8fe9-707b7532174b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; procedurename1 &gt; n&#227;o &#233; poss&#237;vel substituir &lt; procedurename2 &gt; porque diferem nos par&#226;metros declarados como &#39;ParamArray&#39;
Um procedimento em uma classe derivada substitui um procedimento com o mesmo nome na classe base, mas as listas de parâmetros são diferentes.  
  
 Para substituir um procedimento em uma classe herdada, o procedimento de substituição deve corresponder sua lista de parâmetros, o acesso de nível e tipo de retorno \(se houver\). Em particular, ele deve corresponder a qualquer [Opcional](/dotnet/visual-basic/language-reference/modifiers/optional) ou [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray) declaração.  
  
 **ID do erro:** BC30906  
  
### Para corrigir este erro  
  
-   Se você quiser substituir o procedimento, verifique o parâmetro lista exatamente como a lista de parâmetros no procedimento da classe base. Se o último parâmetro é declarado com `ParamArray` no procedimento da classe base, declare\-o com `ParamArray` no procedimento de substituição.  
  
-   Se você quiser uma lista de parâmetros diferente da versão da classe base, você não pode substituí\-la. Considere a sobrecarga em vez disso. Para obter mais informações, consulte [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading).  
  
## Consulte também  
 [Substituições](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)