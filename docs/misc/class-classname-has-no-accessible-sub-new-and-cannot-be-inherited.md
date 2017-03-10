---
title: "Classe &#39;&lt; classname &gt;&#39; n&#227;o tem nenhum &#39;Sub New&#39; acess&#237;vel e n&#227;o pode ser herdada | Microsoft Docs"
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
  - "vbc31399"
  - "BC31399"
helpviewer_keywords: 
  - "BC31399"
ms.assetid: 035b333f-ff6a-4fc4-bd36-82f40b1d8bab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classe &#39;&lt; classname &gt;&#39; n&#227;o tem nenhum &#39;Sub New&#39; acess&#237;vel e n&#227;o pode ser herdada
Uma classe usa um [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement) para especificar uma base de dados de classe, mas não pode acessar nenhum construtor na classe base pretendida.  
  
 Isso pode acontecer se a classe base não tem nenhum construtor ou se ele tiver construtor com níveis de acesso que impeçam o acesso de outra classe.  
  
 Quando você herdar uma classe, o construtor deve chamar o construtor da classe base usando [MyBase \- excluir](http://msdn.microsoft.com/pt-br/52491d06-6451-4f6f-9aa6-8fab59bbc2b9). Se você não fizer essa chamada, ou se você nem mesmo gravar um construtor explícito, Visual Basic gera um construtor implícito que chama `MyBase.New()`.  
  
 **ID do erro:** BC31399  
  
### Para corrigir este erro  
  
1.  Se você tiver o controle de origem sobre a classe base, altere o nível de acesso de pelo menos um dos seus construtores para que outra classe possa acessá\-los.  
  
2.  Se você não pode alterar os níveis de acesso dos construtores de classe base, herde de uma classe diferente ou não.  
  
## Consulte também  
 [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [MyBase \- excluir](http://msdn.microsoft.com/pt-br/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Níveis de acesso no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)