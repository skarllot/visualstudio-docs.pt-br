---
title: "CA2238: implementar m&#233;todos de serializa&#231;&#227;o corretamente | Microsoft Docs"
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
  - "ImplementSerializationMethodsCorrectly"
  - "CA2238"
helpviewer_keywords: 
  - "CA2238"
  - "ImplementSerializationMethodsCorrectly"
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2238: implementar m&#233;todos de serializa&#231;&#227;o corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebra \- se o método é visível fora do assembly.<br /><br /> Sem quebra \- se o método não está visível fora do assembly.|  
  
## Causa  
 Um método que manipula um evento de serialização não possui a assinatura, o tipo de retorno ou a visibilidade corretos.  
  
## Descrição da Regra  
 Um método é designado um manipulador de eventos de serialização aplicando um dos seguintes atributos de evento de serialização:  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
 Os manipuladores de eventos de serialização recebem um único parâmetro do tipo <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, retorna `void` e tem a visibilidade `private` .  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, corrija a assinatura, o tipo de retorno ou a visibilidade do manipulador de eventos de serialização.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra manipuladores de eventos de serialização declarados corretamente.  
  
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-cs[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]  
  
## Regras Relacionadas  
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: implementar ISerializable corretamente](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: proteger construtores de serialização](../Topic/CA2120:%20Secure%20serialization%20constructors.md)