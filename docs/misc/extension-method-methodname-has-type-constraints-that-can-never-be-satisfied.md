---
title: "M&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; tem restri&#231;&#245;es de tipo que nunca podem ser atendidas | Microsoft Docs"
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
  - "bc36561"
  - "vbc36561"
helpviewer_keywords: 
  - "BC36561"
ms.assetid: ff42d6e9-611b-407d-a269-f268b36ed277
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todo de extens&#227;o &#39;&lt; methodname &gt;&#39; tem restri&#231;&#245;es de tipo que nunca podem ser atendidas
Os parâmetros de tipo desse método interajam de forma que impede que nunca ser atendida. O seguinte método de extensão é um exemplo.  
  
```  
'' Not valid. '<Extension()> _ 'Sub extensionExample(Of T As U, U)(ByVal para1 As T, ByVal para2 As U) 'End Sub  
```  
  
 Como o método é um método de extensão, o compilador deve ser capaz de determinar o tipo de dados ou tipos que estende o método com base apenas no primeiro parâmetro na declaração do método, `para1`, e o argumento enviada para esse parâmetro. Quando o primeiro parâmetro refere\-se aos parâmetros de tipo genérico, `para1 as T`, as restrições em parâmetros genéricos restringem o conjunto de tipos para o qual o método se aplica.  
  
 Aplicabilidade de um método de extensão é determinada do argumento fornecido para o primeiro parâmetro, que é `arg1` no código a seguir.  
  
 `'' Not valid.`  
  
 `'arg1.extensionExample(arg2)`  
  
 Deve ser possível verificar as restrições em todos os parâmetros de tipo genérico chamados pelo primeiro parâmetro, `para1`, examinando somente o primeiro argumento, `arg1`. Em `extensionExample`, o conjunto de tipos que está sendo estendido não é possível determinar o primeiro parâmetro sozinho. Parâmetro de tipo `T` é restrito por um parâmetro de tipo `U`, que não é referenciado por `para1` e não pode ser inferido de `arg1`. Portanto, não é possível verificar a aplicabilidade do método para qualquer tipo possíveis e o método nunca pode ser chamado.  
  
 **ID do erro:** BC36561  
  
### Para corrigir este erro  
  
-   Altere a declaração de tipo para remover a interdependência entre os tipos.  
  
## Consulte também  
 [Métodos de extensão](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Tipos genéricos no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)