---
title: "CA2130: as constantes cr&#237;ticas de seguran&#231;a devem ser transparentes | Microsoft Docs"
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
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2130: as constantes cr&#237;ticas de seguran&#231;a devem ser transparentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um campo constante ou um membro de enumeração são marcados com <xref:System.Security.SecurityCriticalAttribute>.  
  
## Descrição da Regra  
 A imposição de transparência não é imposta para valores constantes como valores constantes embutidos dos compiladores de modo que nenhuma pesquisa é necessária em tempo de execução.  Os campos constantes devem ser segurança transparente de forma que os revisores de código não assume que o código transparente não pode acessar a constante.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o atributo de SecurityCritical do campo ou valor.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 Nos exemplos seguintes, o valor `EnumWithCriticalValues.CriticalEnumValue` de enum e `CriticalConstant` constante gerenciem esse aviso.  Para corrigir problemas, remova o atributo de`SecurityCritical`\[\] para fazer a eles a segurança transparente.  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]