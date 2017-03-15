---
title: "CA2133: os representantes devem ser associados a m&#233;todos com transpar&#234;ncia consistente | Microsoft Docs"
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
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2133: os representantes devem ser associados a m&#233;todos com transpar&#234;ncia consistente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
> [!NOTE]
>  Esse aviso é aplicado somente ao código que está executando o CoreCLR \(a versão do CLR que é específica para aplicativos Web do Silverlight\).  
  
## Causa  
 Esse aviso é acionado em um método que associa um representante que é marcado com <xref:System.Security.SecurityCriticalAttribute> a um método que é transparente ou que é marcado com <xref:System.Security.SecuritySafeCriticalAttribute>.  O aviso também será acionado um método que associa um delegado que é transparente seguro\- crítico ou a um método crítico.  
  
## Descrição da Regra  
 Tipos de delegação e métodos que associam no deve ter transparência consistente.  O delega transparentes e seguro\- críticos podem ser associado a outros métodos transparentes ou seguro\- críticos.  Da mesma forma, os representantes críticos podem ser associado aos métodos importantes.  Essas regras de associação garantem que o único código que pode invocar um método através de um representante também poderia ter o mesmo método chamado diretamente.  Por exemplo, as regras de associação impedir que o código transparente chama o código crítico diretamente por meio de um representante transparente.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desse aviso, alterar a transparência de delegação ou do método que associa de forma que a transparência dos dois for equivalente.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
### Código  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]