---
title: "CA1013: sobrecarregar igualdades de operador em add e subtract de sobrecarga | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013: sobrecarregar igualdades de operador em add e subtract de sobrecarga
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um público ou um tipo protegido implementam os operadores de adição ou subtração sem implementar o operador de igualdade.  
  
## Descrição da Regra  
 Quando as instâncias de um tipo podem ser combinadas usando operações como adição e subtração, você deve quase sempre definir a igualdade para retornar `true` para todas as duas instâncias que têm os mesmos valores de.  
  
 Você não pode usar o operador de igualdade padrão em uma implementação sobrecarregada do operador de igualdade.  Isso causará um estouro de pilha.  Para implementar o operador de igualdade, use o método de Object.Equals em sua implementação.  Consulte o exemplo a seguir.  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente o operador de igualdade de modo que ele seja matematicamente consistente com os operadores de adição e subtração.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando a implementação padrão do operador de igualdade fornece o comportamento correto para o tipo.  
  
## Exemplo  
 O exemplo a seguir define um tipo`BadAddableType`\(\) que viola esta regra.  Esse tipo deve implementar o operador de igualdade para fazer todas as duas instâncias que tenham o mesmo teste `true` dos valores de campo para fins de igualdade.  O tipo `GoodAddableType` mostra a implementação fixa.  Observe que esse tipo também implementa o operador de desigualdade e substitui <xref:System.Object.Equals%2A> para as outras regras.  Uma implementação completo também implementaria <xref:System.Object.GetHashCode%2A>.  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## Exemplo  
 O exemplo a seguir testa a igualdade usando instâncias de tipos que foram definidas anteriormente neste tópico para ilustrar o comportamento padrão e correto para o operador de igualdade.  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 O exemplo produz a seguinte saída.  
  
  **Tipo incorreto:  {2,2} {2,2} é igual?  Não**  
**Bom tipo: {3,3} {3,3} é igual?  Sim**  
**Bom tipo: {3,3} {3,3} é \=\=?   Sim**  
**Tipo incorreto:  {2,2} {9,9} é igual?  Não**  
**Bom tipo: {3,3} {9,9} é \=\=?   Não**    
## Consulte também  
 [Operadores de igualdade](../Topic/Equality%20Operators.md)