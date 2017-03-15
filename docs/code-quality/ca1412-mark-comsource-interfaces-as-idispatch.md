---
title: "CA1412: marcar interfaces ComSource como IDispatch | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkComSourceInterfacesAsIDispatch"
  - "CA1412"
helpviewer_keywords: 
  - "CA1412"
  - "MarkComSourceInterfacesAsIDispatch"
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1412: marcar interfaces ComSource como IDispatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkComSourceInterfacesAsIDispatch|  
|CheckId|CA1412|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo é marcado com o atributo de <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> e pelo menos uma interface especificada não é marcada com o conjunto de atributos de <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> ao valor de `InterfaceIsDispatch` .  
  
## Descrição da Regra  
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> é usado para identificar as interfaces de evento que uma classe expõe ao Component Object Model \(COM\) clientes.  Essas interfaces devem ser expostos como `InterfaceIsIDispatch` para permitir que os clientes do Visual Basic 6 COM para receber notificações de eventos.  Por padrão, se uma interface não é marcada com o atributo de <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> , é exposto como uma interface dupla.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicionar ou alterar o atributo de <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> de modo que seu valor é definido como InterfaceIsIDispatch para todas as interfaces que são especificadas com o atributo de <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra uma classe em uma das interfaces viola a regra.  
  
 [!code-cs[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]  
  
## Regras Relacionadas  
 [CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Consulte também  
 [How to: Raise Events Handled by a COM Sink](http://msdn.microsoft.com/pt-br/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)