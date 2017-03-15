---
title: "Tipo ou &#39;New&#39; esperado | Microsoft Docs"
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
  - "vbc32092"
  - "bc32092"
helpviewer_keywords: 
  - "BC32092"
ms.assetid: b3041c1d-837c-4d58-bbb4-5c46f227b66d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo ou &#39;New&#39; esperado
Um parâmetro de tipo na declaração de um tipo genérico apresenta uma lista de restrições com a `As` palavra\-chave, mas não especifica uma restrição válida.  
  
 Uma restrição em um parâmetro de tipo deve ser uma classe válida ou interface ou uma das palavras\-chave `Class`, `Structure`, ou `New`. Se você especificar uma restrição inválida ou nenhum, o compilador gera este erro.  
  
 **ID do erro:** BC32092  
  
### Para corrigir este erro  
  
1.  Determine como o parâmetro de tipo deve ser restrita e especificar a restrição apropriada na lista de restrição.  
  
2.  Se você pretende restringir o parâmetro de tipo por uma classe ou interface, verifique se que a restrição resulta corretamente.  
  
3.  Lembre\-se de separar várias restrições em um parâmetro de tipo único com vírgulas e coloque a lista de restrição entre chaves \(`{ }`\).  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Classe \(Visual Basic\)](http://msdn.microsoft.com/pt-br/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Estrutura \(Visual Basic\)](http://msdn.microsoft.com/pt-br/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)