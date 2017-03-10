---
title: "CA2237: marcar tipos ISerializable com SerializableAttribute | Microsoft Docs"
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
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2237: marcar tipos ISerializable com SerializableAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo externamente visível implementa a interface de <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> e o tipo não é marcado com o atributo de <xref:System.SerializableAttribute?displayProperty=fullName> .  A regra ignora os tipos derivados cujo tipo de base não é serializable.  
  
## Descrição da Regra  
 Para ser reconhecido por Common Language Runtime como serializável, os tipos devem ser marcados com o atributo de <xref:System.SerializableAttribute> mesmo se o tipo usa uma rotina de serialização personalizada com a implementação da interface de <xref:System.Runtime.Serialization.ISerializable> .  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, aplicar o atributo de <xref:System.SerializableAttribute> ao tipo.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra para classes de exceção porque devem ser serializáveis funcionar corretamente pelos domínios de aplicativo.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  Remover a linha do atributo de <xref:System.SerializableAttribute> para atender a regra.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## Regras Relacionadas  
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: implementar ISerializable corretamente](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: proteger construtores de serialização](../Topic/CA2120:%20Secure%20serialization%20constructors.md)