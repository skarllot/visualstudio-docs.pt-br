---
title: "CA1506: evitar acoplamento de classes excessivo | Microsoft Docs"
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
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1506: evitar acoplamento de classes excessivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Categoria|Microsoft.Maintainability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo ou um método são acoplados com muitos outros tipos.  
  
## Descrição da Regra  
 Essa regra se estender pelo envolvimento da classe para contar o número de referências exclusivos do tipo que um tipo ou um método contêm.  
  
 Os tipos e métodos que têm um alto nível do envolvimento da classe podem ser difíceis de manter.  É uma boa prática ter tipos e métodos que exibem baixo acoplamento flexível e a coesão alta.  
  
## Como Corrigir Violações  
 Para corrigir estas violação, tente para reformatar o tipo ou o método para reduzir o número de tipos à qual está associado.  
  
## Quando Suprimir Alertas  
 Exclua esse aviso quando o tipo ou o método são considerados ainda visando independentemente do número grande de dependências em outros tipos.  
  
## Consulte também  
 [Avisos de facilidade de manutenção](../code-quality/maintainability-warnings.md)   
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)