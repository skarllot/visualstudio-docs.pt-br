---
title: "Express&#227;o &#39;AddressOf&#39; n&#227;o pode ser convertido em &#39;&lt; typename &gt;&#39; porque &#39;&lt; typename &gt;&#39; n&#227;o &#233; um tipo delegado | Microsoft Docs"
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
  - "vbc30581"
  - "bc30581"
helpviewer_keywords: 
  - "BC30581"
ms.assetid: 5db7589a-5456-4b3a-9d6b-93d9157f0484
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o &#39;AddressOf&#39; n&#227;o pode ser convertido em &#39;&lt; typename &gt;&#39; porque &#39;&lt; typename &gt;&#39; n&#227;o &#233; um tipo delegado
Uma instrução tenta converter um `AddressOf` expressão em um tipo que não é um tipo delegado.  
  
 O `AddressOf` operador cria uma instância delegada de procedimento que faz referência a um procedimento específico.`AddressOf` pode ser usado como o operando do construtor delegado, ou ele pode ser usado em um contexto no qual o tipo do delegado pode ser determinado pelo compilador.  
  
 **ID do erro:** BC30581  
  
### Para corrigir este erro  
  
-   Altere o tipo de destino para um tipo delegado.  
  
## Consulte também  
 [Operador AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)