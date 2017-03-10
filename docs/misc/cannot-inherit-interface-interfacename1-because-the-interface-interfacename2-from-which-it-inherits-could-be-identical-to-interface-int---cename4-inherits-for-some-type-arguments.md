---
title: "N&#227;o &#233; poss&#237;vel herdar a interface &#39;&lt; interfacename1 &gt;&#39; porque a interface &#39;&lt; interfacename2 &gt;&#39; da qual ela herda pode ser id&#234;ntica &#224; interface &#39;&lt; interfacename3 &gt;&#39; da qual a interface &#39;&lt; interfacename4 &gt;&#39; herda para alguns argumentos de tipo | Microsoft Docs"
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
  - "vbc32122"
  - "bc32122"
helpviewer_keywords: 
  - "BC32122"
ms.assetid: 64a66ec7-0f5f-4804-a92b-9a6279fdfd6d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel herdar a interface &#39;&lt; interfacename1 &gt;&#39; porque a interface &#39;&lt; interfacename2 &gt;&#39; da qual ela herda pode ser id&#234;ntica &#224; interface &#39;&lt; interfacename3 &gt;&#39; da qual a interface &#39;&lt; interfacename4 &gt;&#39; herda para alguns argumentos de tipo
Uma interface genérica herda de duas ou mais interfaces genéricas, e duas das heranças poderiam conflitar por certo valores de argumentos de tipo.  
  
 As instruções a seguir podem gerar esse erro.  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface interfaceY(Of w) Inherits interfaceA(Of w) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceX(Of t1), interfaceY(Of t2) End Interface  
```  
  
 Se `derivedInterface` é construída ou implementada fornecendo o mesmo tipo para ambos `t1` e `t2`, ela deve herdar duas versões do `interfaceA` com argumentos de tipo idênticos. Isso produziria uma ambigüidade sobre qual versão acessar.  
  
 **ID do erro:** BC32122  
  
### Para corrigir este erro  
  
-   Altere um dos argumentos de tipo fornecidos a interface derivada para que não haja nenhum conflito.  
  
     \- ou \-  
  
-   Remova o `Inherits` instrução das interfaces causando o potencial conflito de herança ou implementação.  
  
## Consulte também  
 [NÃO está em compilação: Visão geral de Interfaces](http://msdn.microsoft.com/pt-br/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Instrução Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)