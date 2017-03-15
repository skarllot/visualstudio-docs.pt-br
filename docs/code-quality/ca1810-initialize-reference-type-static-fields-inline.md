---
title: "CA1810: inicializar campos est&#225;ticos de tipo de refer&#234;ncia embutido | Microsoft Docs"
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
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1810: inicializar campos est&#225;ticos de tipo de refer&#234;ncia embutido
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo de referência declara um construtor estático explícito.  
  
## Descrição da Regra  
 Quando um tipo declara um construtor estático explícito, o compilador de \(JIT\) just\-in\-time adiciona uma verificação a cada construtor de método estático e da instância do tipo para garantir que o construtor estático esteve chamado anteriormente.  A inicialização estático é disparada quando qualquer membro estático é acessado ou quando uma instância do tipo é criada.  No entanto, a inicialização estático não será disparada se você a seguir declara uma variável do tipo mas não o usa o, que pode ser importante se a inicialização altera o estado global.  
  
 Quando todos os dados estáticos forem embutidos inicializado e um construtor estático explícito não esteja declarado, os compiladores de linguagem intermediária da Microsoft \(MSIL\) adiciona o sinalizador de `beforefieldinit` e um construtor estático implícito, que inicializa os dados estáticos, definição de tipo de MSIL.  Quando o compilador JIT encontrar o sinalizador de `beforefieldinit` , as verificações estáticos de construtor não serão adicionadas na maioria das vezes.  A inicialização estático é garantida para ocorrer em qualquer dia antes que todos os campos estáticos são acessadas mas não antes que um construtor de método estático ou da instância seja invocado.  Observe que a inicialização estático pode ocorrer a qualquer momento depois que uma variável de tipo é declarado.  
  
 As verificações estáticos de construtor podem diminuir o desempenho.  Um construtor estático é frequentemente usado para inicializar somente campos estáticos nesse caso, você só deve assegurar que a inicialização estático ocorre antes do primeiro acesso de um campo estático.  O comportamento de `beforefieldinit` é adequado para esses e a maioria dos outros tipos.  Inadequado é somente quando a inicialização estático afeta o estado global e um dos seguintes for verdadeiro:  
  
-   O efeito no estado global é caro e não será necessário se o tipo não é usado.  
  
-   Os efeitos globais do estado podem ser acessados sem acessar os campos estáticos do tipo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, inicializar todos os dados estáticos quando é declarada e remover o construtor estático.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra não se o desempenho for uma preocupação; ou se as alterações de estado global que são causadas pela inicialização estático são onerosas ou devem ser garantido acontecer antes de um método de tipo estático ser chamado ou uma instância do tipo é criada.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo, `StaticConstructor`, que viola a regra e um tipo, `NoStaticConstructor`, que substitui o construtor estático com a inicialização embutida para atender a regra.  
  
 [!CODE [FxCop.Performance.RefTypeStaticCtor#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor#1)]  
  
 Observe a adição do sinalizador de `beforefieldinit` na definição de MSIL para a classe de `NoStaticConstructor` .  
  
  **ANSI utilitário StaticConstructor auto da classe**  
 **estende \[\] System.Object mscorlib**  
**{**  
**} extremidade do \/\/da classe StaticConstructor**  
**beforefieldinit utilitário NoStaticConstructor ansi auto da classe**  
 **estende \[\] System.Object mscorlib**  
**{**  
**} extremidade do \/\/da classe NoStaticConstructor**   
## Regras Relacionadas  
 [CA2207: inicializar campos estáticos de tipo de valor embutido](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)