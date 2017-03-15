---
title: "CA1402: evitar sobrecargas em interfaces vis&#237;veis COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402: evitar sobrecargas em interfaces vis&#237;veis COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Uma interface visível do Component Object Model \(COM\) declara métodos sobrecarregados.  
  
## Descrição da Regra  
 Quando os métodos sobrecarregados são expostos para clientes COM, apenas a primeira sobrecarga do método retém seu nome.  As sobrecargas subsequentes são renomeadas exclusivamente acrescentando\-se ao nome um caractere de sublinhado “\_” e um inteiro que corresponde à ordem de declaração de sobrecarga.  Por exemplo, considere os seguintes métodos.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Esses métodos são expostos para clientes COM com o seguinte.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Os clientes do Visual Basic 6 COM não podem implementar métodos da interface usando um sublinhado no nome.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, renomeie os métodos sobrecarregados de forma que os nomes são exclusivos.  Como alternativa, crie a interface invisível COM a alteração da acessibilidade a `internal` \(`Friend` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) ou aplicando o atributo de <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false`.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra uma interface que viola a regra e uma interface que satisfaça a regra.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## Regras Relacionadas  
 [CA1413: evitar campos não públicos em tipos de valor visíveis COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: evitar membros estáticos em tipos visíveis COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Consulte também  
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Tipo de dados Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)