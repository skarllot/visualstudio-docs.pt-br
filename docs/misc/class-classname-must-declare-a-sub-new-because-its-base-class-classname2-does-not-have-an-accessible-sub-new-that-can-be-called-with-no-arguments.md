---
title: "Classe &#39;&lt; classname &gt;&#39; deve declarar um &#39;Sub New&#39; porque sua classe base &#39;&lt; classname2 &gt;&#39; n&#227;o tem um &#39;Sub New&#39; acess&#237;vel que pode ser chamado sem argumentos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30387"
  - "bc30387"
helpviewer_keywords: 
  - "BC30387"
ms.assetid: ff587e79-fa47-4b55-9a08-24688b209e0a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classe &#39;&lt; classname &gt;&#39; deve declarar um &#39;Sub New&#39; porque sua classe base &#39;&lt; classname2 &gt;&#39; n&#227;o tem um &#39;Sub New&#39; acess&#237;vel que pode ser chamado sem argumentos
Uma classe derivada não declara um construtor, e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não é possível gerar um porque não há nenhum construtor de classe base pode chamar.  
  
 Quando uma classe derivada não declara um construtor, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tenta gerar um construtor implícito sem parâmetros que chama `MyBase.New()`. Se não houver nenhum construtor acessível na classe base que pode ser chamado sem argumentos, ou se houver mais de um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não é possível gerar um construtor implícito.  
  
 **ID do erro:** BC30387  
  
### Para corrigir este erro  
  
1.  Declare e implemente pelo menos um `Sub New` construtor em algum lugar na classe derivada.  
  
2.  Adicione uma chamada para um construtor de classe base, `MyBase.New()`, como a primeira linha de cada `Sub New`.  
  
## Consulte também  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [Opcional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Parâmetros opcionais](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)   
 [Matrizes de parâmetros](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)