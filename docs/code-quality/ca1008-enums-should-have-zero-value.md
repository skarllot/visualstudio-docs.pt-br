---
title: "CA1008: os enums devem ter valor zero | Microsoft Docs"
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
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1008: os enums devem ter valor zero
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem\-quebras \- quando for solicitado a adicionar um valor de **Nenhum** a uma enumeração de não sinalizador. Interromper \- quando for solicitado a renomear ou remover todos os valores da enumeração.|  
  
## Causa  
 Uma enumeração sem <xref:System.FlagsAttribute?displayProperty=fullName> aplicado não definir um membro que tinha um valor de zero; ou uma enumeração que tem <xref:System.FlagsAttribute> aplicado não definir um membro que tinha um valor de zero mas seu nome for “nenhuma”\), ou a enumeração definirá membros zero valor múltiplo.  
  
## Descrição da Regra  
 O valor padrão de uma enumeração não inicializadas, exatamente como outros tipos de valor, é zero.  Uma enumeração non\-flags−attributed deve definir um membro que possui o valor de zero de forma que o valor padrão é um valor válido da enumeração.  Se apropriado, o nome do membro “nenhum”.  Se não, atribua zero com mais frequência ao membro usado.  Observe que, por padrão, se o valor do primeiro membro de enumeração não for definido na declaração, seu valor é zero.  
  
 Se uma enumeração que tem <xref:System.FlagsAttribute> aplicado define um valor de zero membro, seu nome não deve ser “nenhum” para indicar que nenhum valor esteve definido na enumeração.  Usar um membro sem valor de para qualquer outra finalidade é do contador ao uso de <xref:System.FlagsAttribute> que AND e OR operadores bit a bit são inúteis com o membro.  Isso significa que somente um membro deve ser atribuído o valor zero.  Observe que se vários membros que têm o valor zero ocorrer em uma enumeração sinalizador\- alocada, `Enum.ToString()` retornam resultados incorretos para membros que não são zero.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra para enumerações non\-flags−attributed, defina um membro que possui o valor de zero; essa é uma alteração não recentes.  Para enumerações sinalizador\- atribuídas que definem um membro zero, o valor desse membro “nenhum” e exclui todos os outros membros que têm um valor de zero; essa é uma alteração.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra com exceção das enumerações sinalizador\- atribuídas que têm enviado anteriormente.  
  
## Exemplo  
 O exemplo a seguir mostra duas enumerações que satisfazem a regra e uma enumeração, `BadTraceOptions`, que viola a regra.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## Regras Relacionadas  
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: não nomeie valores de enum como 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: não use valores enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: o armazenamento de enum deve ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Consulte também  
 <xref:System.Enum?displayProperty=fullName>