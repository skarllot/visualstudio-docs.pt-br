---
title: "CA2229: implementar construtores de serializa&#231;&#227;o | Microsoft Docs"
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
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2229: implementar construtores de serializa&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 O tipo implementa a interface de <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> , não é um representante ou uma interface, e uma das seguintes condições for verdadeira:  
  
-   O tipo não tem um construtor que usa um objeto de <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> e um objeto de <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> \(assinatura do construtor de serialização\).  
  
-   O tipo é não lacrado e o modificador de acesso para o construtor de serialização não é seguro \(família\).  
  
-   O tipo é selado e o modificador de acesso para o construtor de serialização não será privado.  
  
## Descrição da Regra  
 Esta regra é relevante para os tipos que dão suporte a serialização personalizada.  Um tipo oferecer suporte a serialização personalizada que implementa a interface de <xref:System.Runtime.Serialization.ISerializable> .  O construtor de serialização é necessário desserializar, ou recrie os objetos que foram serializado usando o método de <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> .  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente o construtor de serialização.  Para uma classe selada, faça o construtor particular; se não, remova protegida.  
  
## Quando Suprimir Alertas  
 Não suprima uma violação da regra.  O tipo não será deserializable, e não funcionará em muitos cenários.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que satisfaça a regra.  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## Regras Relacionadas  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Consulte também  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>