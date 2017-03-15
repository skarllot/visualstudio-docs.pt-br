---
title: "CA2208: instanciar exce&#231;&#245;es de argumento corretamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2208: instanciar exce&#231;&#245;es de argumento corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 As causas possíveis incluem as seguintes situações:  
  
-   For feita uma chamada para o construtor \(sem parâmetros\) padrão de um tipo de exceção ou seja, ou é derivado de [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True).  
  
-   Um argumento incorreto de cadeia de caracteres é passado a um construtor com parâmetros de um tipo de exceção ou seja, ou é derivado de [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True)  
  
## Descrição da Regra  
 Em vez de chamar o construtor padrão, chame uma das sobrecargas do construtor que permite que uma mensagem de exceção mais significativo é fornecida.  A mensagem de exceção deve ter como destino o desenvolvedor e claramente explicar a condição de erro e como corrigir ou impedir a exceção.  
  
 As assinaturas de um e dois construtores de cadeia de caracteres de <xref:System.ArgumentException> e seus tipos derivados não são consistentes em relação aos parâmetros de `message` e de `paramName` .  Verifique se estes construtores são chamados com os argumentos corretos de cadeia de caracteres.  As assinaturas são os seguintes:  
  
 <xref:System.ArgumentException>\(cadeia de caracteres `message`\)  
  
 <xref:System.ArgumentException>\(cadeia de caracteres `message`, cadeia de caracteres `paramName`\)  
  
 <xref:System.ArgumentNullException>\(cadeia de caracteres `paramName`\)  
  
 <xref:System.ArgumentNullException>\(cadeia de caracteres `paramName`, cadeia de caracteres `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(cadeia de caracteres `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(cadeia de caracteres `paramName`, cadeia de caracteres `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(cadeia de caracteres `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(cadeia de caracteres `parameterName`, cadeia de caracteres `message`\)  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, chamar um construtor que usa uma mensagem, um nome de parâmetro, ou ambos, e verifique se os argumentos são apropriadas para o tipo de <xref:System.ArgumentException> que está sendo chamado.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra apenas se um construtor com parâmetros é chamado com os argumentos corretos de cadeia de caracteres.  
  
## Exemplo  
 O exemplo a seguir mostra um construtor que cria uma instância incorretamente uma instância do tipo de ArgumentNullException.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## Exemplo  
 O exemplo a seguir corrige a violação acima alternando os argumentos de construtor.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]