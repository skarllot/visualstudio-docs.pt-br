---
title: "CA1019: definir acessadores para argumentos de atributo | Microsoft Docs"
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
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019: definir acessadores para argumentos de atributo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 No construtor, um atributo define os argumentos que não têm propriedades correspondentes.  
  
## Descrição da Regra  
 Os atributos podem definir argumentos obrigatórios que devem ser especificados quando você aplicar o atributo a um destino.  Eles também são conhecidos como argumentos posicionais porque são fornecidas para atribuir construtores como parâmetros posicionais.  Para cada argumento obrigatório, o atributo deve fornecer uma propriedade somente leitura correspondente de forma que o valor do argumento pode ser recuperado em tempo de execução.  Esta regra verifica o que para cada parâmetro do construtor, você definiu a propriedade correspondente.  
  
 Os atributos também podem definir argumentos opcionais, que também são conhecidos como argumentos nomeados.  Esses argumentos são fornecidos para atribuir por nome construtores e devem ter uma propriedade de leitura\/gravação correspondente.  
  
 Para argumentos obrigatórios e opcionais, as propriedades e os parâmetros correspondentes do devem usar o mesmo nome mas a diferença em.  O uso de maiúsculas e minúsculas de Pascal de uso de propriedades, e os parâmetros usam as caixas de camelo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione uma propriedade somente leitura para cada parâmetro do construtor que não tem um.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se não quiser que o valor do argumento obrigatório para ser recuperável.  
  
## Exemplo de atributos personalizados  
  
### Descrição  
 O exemplo a seguir mostra dois atributos que definem um parâmetro posicional \(obrigatório\).  A primeira implementação do atributo for definida incorretamente.  A segunda implementação está correta.  
  
### Código  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## Argumento posicional e nomeado  
  
### Descrição  
 Os argumentos posicionais e nomeadas fazem para limpar para consumidores da biblioteca que os argumentos são obrigatórios para o atributo e os argumentos que são opcionais.  
  
 O exemplo a seguir mostra uma implementação de um atributo que tem argumentos posicionais e nomeadas.  
  
### Código  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### Comentários  
 O exemplo a seguir mostra como aplicar o atributo personalizado a duas propriedades.  
  
### Código  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## Regras Relacionadas  
 [CA1813: evitar atributos não lacrados](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Consulte também  
 [Atributos](../Topic/Attributes1.md)