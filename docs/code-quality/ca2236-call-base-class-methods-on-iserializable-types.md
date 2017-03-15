---
title: "CA2236: chamar m&#233;todos de classe base em tipos ISerializable | Microsoft Docs"
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
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2236: chamar m&#233;todos de classe base em tipos ISerializable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo é derivado de um tipo que implementa a interface de <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> , e uma das seguintes condições for verdadeira:  
  
-   O tipo implementa o construtor de serialização, isto é, um construtor com <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, assinatura do parâmetro de <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> , mas não chama o construtor de serialização do tipo de base.  
  
-   O tipo implementa o método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> mas não chama o método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> do tipo de base.  
  
## Descrição da Regra  
 Em um processo de serialização personalizada, um tipo implementa o método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> para serializar seus campos e o construtor de serialização MDS para serializar os campos.  Se o tipo se deriva de um tipo que implementa a interface de <xref:System.Runtime.Serialization.ISerializable> , o construtor do método e de serialização do <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> do tipo de base deve ser chamado a serialize\/de\-serialize os campos de tipo base.  Caso contrário, o tipo não será serializado e o MDS não será serializado corretamente.  Observe que se o tipo derivado não adiciona os novos campos, o tipo não precisa implementar o método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nem o construtor de serialização ou de chamar os equivalentes do tipo de base.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame o método ou do construtor de serialização do <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> do tipo de base do método correspondentes derivado do tipo ou o construtor.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo derivado que satisfaça a regra chamando o método do construtor e de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> de serialização da classe base.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## Regras Relacionadas  
 [CA2240: implementar ISerializable corretamente](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: proteger construtores de serialização](../Topic/CA2120:%20Secure%20serialization%20constructors.md)