---
title: "&#39;&lt; nome do membro &gt;&#39; n&#227;o pode implementar &#39; &lt; interfacename &gt;. &lt; interfacemembername &gt;&#39; porque eles diferem por restri&#231;&#245;es de par&#226;metro de tipo | Microsoft Docs"
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
  - "vbc32078"
  - "BC32078"
helpviewer_keywords: 
  - "BC32078"
ms.assetid: 2c971345-edb4-491e-9202-8eb8286b66f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; nome do membro &gt;&#39; n&#227;o pode implementar &#39; &lt; interfacename &gt;. &lt; interfacemembername &gt;&#39; porque eles diferem por restri&#231;&#245;es de par&#226;metro de tipo
Um evento genérico, propriedade ou procedimento tenta implementar um membro similar definido em uma interface, mas eles têm diferentes listas de restrições em seus parâmetros de tipo.  
  
 Para implementar um membro de interface, o membro implementando deve corresponder não apenas a assinatura completa do membro da interface, mas também o mecanismo de passagem de cada parâmetro.  
  
 Para implementar um membro de interface genérica, o membro implementando deve adicionalmente coincidir com o número de parâmetros de tipo e a lista de restrições de cada um deles.  
  
 Para obter detalhes sobre a implementação da interface, consulte [não está em compilação: palavra\-chave Implements e instrução Implements](http://msdn.microsoft.com/pt-br/b96560f7-6413-480f-a1e2-f80253bab5be).  
  
 **ID do erro:** BC32078  
  
### Para corrigir este erro  
  
-   Se você pretende implementar o membro de interface, revise as restrições de parâmetro de tipo para coincidir com os do membro da interface.  
  
-   Se as restrições de parâmetro de tipo devem permanecer como estão, você não pode implementar o membro de interface nessa declaração. Remover o [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) palavra\-chave da declaração.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NÃO está em compilação: Exemplos de implementação de Interface no Visual Basic](http://msdn.microsoft.com/pt-br/50bf2a30-73b6-4126-a921-075fd6eec278)