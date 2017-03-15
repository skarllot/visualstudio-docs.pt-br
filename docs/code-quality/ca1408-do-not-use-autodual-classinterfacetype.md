---
title: "CA1408: n&#227;o usar AutoDual ClassInterfaceType | Microsoft Docs"
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
  - "DoNotUseAutoDualClassInterfaceType"
  - "CA1408"
helpviewer_keywords: 
  - "CA1408"
  - "DoNotUseAutoDualClassInterfaceType"
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1408: n&#227;o usar AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo visível do Component Object Model \(COM\) é marcado com atributo definido de <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ao valor de `AutoDual` de <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## Descrição da Regra  
 Tipos que usa uma interface dupla permite que clientes para associar a um layout específico da interface.  Todas as modificações em uma versão futura ao layout do tipo ou de qualquer tipo de base do travará clientes COM que são associados à interface.  Por padrão, se o atributo de <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> não for especificado, uma interface de expedição somente é usada.  
  
 A menos que marcados de outra forma, todos os tipos públicos não são visíveis à; todos os tipos genéricos público e são invisíveis COM.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o valor do atributo de <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ao valor de `None` de <xref:System.Runtime.InteropServices.ClassInterfaceType> e defina explicitamente a interface.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra a menos que seja absolutamente certeza de que o layout do tipo e seus tipos de base não será alterado em uma versão futura.  
  
## Exemplo  
 O exemplo a seguir mostra uma classe que viola a regra e novamente uma declaração de classe para usar uma interface explícita.  
  
 [!code-cs[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## Regras Relacionadas  
 [CA1403: os tipos de layout automático não devem ser visíveis em COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412: marcar interfaces ComSource como IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## Consulte também  
 [Introducing the Class Interface](http://msdn.microsoft.com/pt-br/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualificando tipos do .NET para interoperação](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)