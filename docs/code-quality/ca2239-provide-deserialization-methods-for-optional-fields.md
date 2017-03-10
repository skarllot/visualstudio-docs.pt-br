---
title: "CA2239: fornecer m&#233;todos de desserializa&#231;&#227;o para campos opcionais | Microsoft Docs"
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
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2239: fornecer m&#233;todos de desserializa&#231;&#227;o para campos opcionais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo tem um campo que é marcado com o atributo de <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> e o tipo não fornece métodos de manipulação de eventos de desserialização.  
  
## Descrição da Regra  
 O atributo de <xref:System.Runtime.Serialization.OptionalFieldAttribute> não tem nenhum efeito na serialização; um campo marcado com o atributo é serializado.  No entanto, o campo é ignorado na desserialização e retém o valor padrão associado ao tipo.  Os manipuladores de eventos de desserialização devem ser declarados para definir o campo durante o processo de desserialização.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicionar métodos de manipulação de eventos de desserialização para o tipo.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o campo é ignorado durante o processo de desserialização.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo com métodos de manipulação de um campo opcional e do evento de desserialização.  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## Regras Relacionadas  
 [CA2236: chamar métodos de classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: implementar ISerializable corretamente](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)  
  
 [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: proteger construtores de serialização](../Topic/CA2120:%20Secure%20serialization%20constructors.md)