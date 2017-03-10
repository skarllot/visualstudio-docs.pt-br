---
title: "&#39;Global&#39; n&#227;o permitido neste contexto; Identificador esperado | Microsoft Docs"
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
  - "vbc36001"
  - "bc36001"
helpviewer_keywords: 
  - "BC36001"
ms.assetid: d515daa2-f53d-424c-81fd-e9c4b12f331b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; n&#227;o permitido neste contexto; Identificador esperado
O `Global` palavra\-chave é usada em uma instrução em que não é permitido.  
  
 O `Global` palavra\-chave permite que você acesse um namespace definido fora da hierarquia de namespace no qual seu código deve ser compilado.`Global` Inicia o caminho de qualificação no nível de namespace mais externo da biblioteca de classes do .NET Framework. Para obter uma ilustração, consulte [Global \- excluir](http://msdn.microsoft.com/pt-br/18c8ba14-40f6-4978-8096-6a5852324635).  
  
 Determinadas instruções, como `Imports` e `Namespace`, são independentes do namespace no qual seu código deve ser compilado. Eles exigem um caminho de qualificação completa, a partir do namespace no nível raiz, como <xref:System> ou <xref:Microsoft.VisualBasic>. Em tais declarações, a `Global` palavra\-chave é supérfluo e não é permitido.  
  
 **ID do erro:** BC36001  
  
### Para corrigir este erro  
  
-   Remover o `Global` palavra\-chave da declaração. Não é necessária.  
  
## Consulte também  
 [Global \- excluir](http://msdn.microsoft.com/pt-br/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Instrução Imports \(tipo e namespace .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Instrução Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Referências e a instrução Imports](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)