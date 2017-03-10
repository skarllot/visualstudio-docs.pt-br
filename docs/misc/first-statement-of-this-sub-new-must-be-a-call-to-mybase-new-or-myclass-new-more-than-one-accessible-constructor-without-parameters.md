---
title: "A primeira instru&#231;&#227;o deste &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (mais de um construtor acess&#237;vel sem par&#226;metros) | Microsoft Docs"
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
  - "vbc32038"
  - "bc32038"
helpviewer_keywords: 
  - "BC32038"
ms.assetid: 52e4e9df-a85b-46ae-a0cc-7d8fa377fe95
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A primeira instru&#231;&#227;o deste &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (mais de um construtor acess&#237;vel sem par&#226;metros)
A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' porque a classe base '\< base \>' de '\< derived \>' tem mais de um 'Sub New' acessível que pode ser chamado sem argumentos.  
  
 Um construtor de classe não fornece uma chamada para um construtor de classe base, e [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] não pode fornecer uma chamada implícita porque não é possível determinar qual construtor de classe base chamar.  
  
 **ID do erro:** BC32038  
  
### Para corrigir este erro  
  
-   Adicione uma chamada para um construtor de classe base `MyBase.New()`, ou a outro construtor dessa classe usando `MyClass.New()` ou `Me.New()`, como a primeira linha desse construtor.  
  
## Consulte também  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [MyBase \- excluir](http://msdn.microsoft.com/pt-br/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)