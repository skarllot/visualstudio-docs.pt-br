---
title: "Option Strict On n&#227;o permite restri&#231;&#227;o em convers&#245;es de tipo impl&#237;cito entre o m&#233;todo de extens&#227;o &#39;&lt; extensionmethodname &gt;&#39; definido em &#39;&lt; modulename &gt;&#39; e o delegado &#39;&lt; nomedelegado &gt;&#39; | Microsoft Docs"
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
  - "bc36709"
  - "vbc36709"
helpviewer_keywords: 
  - "BC36709"
ms.assetid: 95d8c833-3525-411b-98e8-b7d3f61f75c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n&#227;o permite restri&#231;&#227;o em convers&#245;es de tipo impl&#237;cito entre o m&#233;todo de extens&#227;o &#39;&lt; extensionmethodname &gt;&#39; definido em &#39;&lt; modulename &gt;&#39; e o delegado &#39;&lt; nomedelegado &gt;&#39;
Com `Option Strict` você não pode ter uma conversão de restrição do tipo de dados de um parâmetro em um representante para o parâmetro correspondente de um método de extensão atribuído a uma variável do tipo delegado. O tipo de dados do parâmetro de representante deve ampliar para o tipo de dados do método de extensão.  
  
 **ID do erro:** BC36709  
  
### Para corrigir este erro  
  
-   Altere o tipo de dados do parâmetro em que o representante ou o método de extensão para que a relação de ampliação necessária exista.  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Conversão de delegado reduzida](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)