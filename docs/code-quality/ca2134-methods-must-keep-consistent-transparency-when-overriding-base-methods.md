---
title: "CA2134: os m&#233;todos devem manter uma transpar&#234;ncia consistente durante a substitui&#231;&#227;o dos m&#233;todos base | Microsoft Docs"
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
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134: os m&#233;todos devem manter uma transpar&#234;ncia consistente durante a substitui&#231;&#227;o dos m&#233;todos base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Esta regra é disparada quando um método marcado com <xref:System.Security.SecurityCriticalAttribute> substitui um método que é transparente ou marcado com <xref:System.Security.SecuritySafeCriticalAttribute>.  A regra também é acionado quando um método que é transparente ou marcado com <xref:System.Security.SecuritySafeCriticalAttribute> substitui um método que está marcado com <xref:System.Security.SecurityCriticalAttribute>.  
  
 A regra é aplicada ao substituir um método virtual ou ao implementar uma interface.  
  
## Descrição da Regra  
 Esta regra é acionado em tenta alterar a acessibilidade de segurança de um método mais acima da cadeia de herança.  Por exemplo, se um método virtual em uma classe base é transparente ou seguro\- crítico, a classe derivada deve ser substituído pelo método ou transparente seguro\- crítico.  Entretanto, se o virtual é crítico segurança, a classe derivada deve ser substituído pelo método crítico de segurança.  A mesma regra se aplica implementando métodos da interface.  
  
 As regras de transparência são impostas quando o código é JIT compilado em vez de em tempo de execução, de modo que o cálculo de transparência não tenha as informações de tipo dinâmico.  Em virtude disso, o resultado de cálculo de transparência deve poder ser determinado somente os tipos estáticos sendo compilados, independentemente do tipo dinâmico.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, alterar a transparência do método que está substituindo um método virtual ou estiver implementando uma interface para corresponder à transparência do método virtual ou da interface.  
  
## Quando Suprimir Alertas  
 Não suprima avisos desta regra.  As violações desta regra resultarão em um tempo de execução <xref:System.TypeLoadException> para assemblies que usam a transparência de nível 2.  
  
## Exemplos  
  
### Código  
 [!CODE [FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency#1)]  
  
## Consulte também  
 [Código transparente de segurança, nível 2](../Topic/Security-Transparent%20Code,%20Level%202.md)