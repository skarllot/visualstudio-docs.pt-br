---
title: "CA2235: marcar todos os campos n&#227;o serializ&#225;veis | Microsoft Docs"
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
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2235: marcar todos os campos n&#227;o serializ&#225;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um campo da instância de um tipo que não seja serializável é declarado em um tipo que é serializable.  
  
## Descrição da Regra  
 Um tipo serializável é um que é marcado com o atributo de <xref:System.SerializableAttribute?displayProperty=fullName> .  Quando o tipo é serializado de <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> , uma exceção será gerada se um tipo que contém um campo da instância de um tipo que não seja serializável.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, aplicar o atributo de <xref:System.NonSerializedAttribute?displayProperty=fullName> ao campo que não seja serializável.  
  
## Quando Suprimir Alertas  
 Suprima apenas um aviso dessa regra se um tipo de <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> é declarado que permite que as instâncias do campo são serializadas e desserializado.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra e um tipo que satisfaça a regra.  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## Regras Relacionadas  
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: implementar ISerializable corretamente](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: proteger construtores de serialização](../Topic/CA2120:%20Secure%20serialization%20constructors.md)