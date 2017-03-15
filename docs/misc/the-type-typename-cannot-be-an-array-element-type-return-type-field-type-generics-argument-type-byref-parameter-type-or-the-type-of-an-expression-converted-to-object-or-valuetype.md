---
title: "O tipo &#39;&lt; typename &gt;&#39; n&#227;o pode ser um tipo de elemento de matriz, o tipo de retorno, o tipo de campo, o argumento gen&#233;ricos tipo, tipo de par&#226;metro &#39;ByRef&#39; ou o tipo de uma express&#227;o convertido em &#39;Object&#39; ou &#39;ValueType&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31396"
  - "BC31396"
helpviewer_keywords: 
  - "BC31396"
ms.assetid: 56998a2c-a705-482e-87ee-5eff707f8a48
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; n&#227;o pode ser um tipo de elemento de matriz, o tipo de retorno, o tipo de campo, o argumento gen&#233;ricos tipo, tipo de par&#226;metro &#39;ByRef&#39; ou o tipo de uma express&#227;o convertido em &#39;Object&#39; ou &#39;ValueType&#39;
Uma expressão declara uma variável, parâmetro de procedimento, parâmetro de tipo, função de retorno ou matriz de um tipo restrito.  
  
 O common language runtime \(CLR\) expõe determinados tipos exclusivamente para suporte de idioma especial, e eles não devem ser usados como tipos de dados em seu aplicativo. Esses tipos incluem o <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, e <xref:System.TypedReference> estruturas.  
  
 **ID do erro:** BC31396  
  
### Para corrigir este erro  
  
-   Não use a estrutura restrita como um tipo de dados declarado.  
  
## Consulte também  
 <xref:System.ArgIterator>   
 <xref:System.RuntimeArgumentHandle>   
 <xref:System.TypedReference>