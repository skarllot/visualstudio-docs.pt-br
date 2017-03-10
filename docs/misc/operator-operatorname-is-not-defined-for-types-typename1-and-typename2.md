---
title: "Operador &#39;&lt; operatorname &gt;&#39; n&#227;o est&#225; definido para tipos &#39;&lt; typename1 &gt;&#39; e &#39;&lt; typename2 &gt;&#39; | Microsoft Docs"
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
  - "vbc31080"
  - "bc31080"
helpviewer_keywords: 
  - "BC31080"
ms.assetid: d2f77450-2bf2-4b1e-b95f-dbc7878f2777
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador &#39;&lt; operatorname &gt;&#39; n&#227;o est&#225; definido para tipos &#39;&lt; typename1 &gt;&#39; e &#39;&lt; typename2 &gt;&#39;
Operador '\< operatorname \>' não está definido para tipos '\< typename1 \>' e '\< typename2 \>'. Use o operador 'Is' para comparar dois tipos de referência.  
  
 Foi feita uma tentativa para usar um operador de forma que não seja apropriada para os tipos especificados. Esse erro pode ser causado por usando o operador "\=" em vez de usar o `Is` operador para comparar dois objetos.  
  
 **ID do erro:** BC31080  
  
### Para corrigir este erro  
  
1.  Use `Is` operador para comparar dois tipos de referência.  
  
2.  Use o `Not` operador em conjunto com o `Is` operador para denotar desigualdade. Por exemplo:  
  
     [!code-vb[VbVbalrOOP#89](../misc/codesnippet/VisualBasic/operator-operatorname-is-not-defined-for-types-typename1-and-typename2_1.vb)]  
  
## Consulte também  
 [Operador Is](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Operador \=](/dotnet/visual-basic/language-reference/operators/assignment-operator)   
 [Operador Not](/dotnet/visual-basic/language-reference/operators/not-operator)