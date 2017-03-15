---
title: "CA2211: os campos n&#227;o constantes n&#227;o devem estar vis&#237;veis | Microsoft Docs"
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
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2211: os campos n&#227;o constantes n&#227;o devem estar vis&#237;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um campo estático protegido não são constantes ou é somente leitura.  
  
## Descrição da Regra  
 Os campos estáticos que não são constantes ou somente leitura não é seguro para threads.  O acesso a esse campo deve ser cuidadosamente controlado exige e técnicas de programação avançado para sincronizar o acesso ao objeto da classe.  Como essas são difíceis a aprender habilidades e dominar, e testando tais representa um objeto de seus próprios desafios, os campos estáticos são usados melhor para armazenar os dados que não são alterados.  Essa regra se aplica às bibliotecas; os aplicativos não devem expor os campos.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, faça a constante estático do campo ou somente leitura.  Se isso não for possível, recrie os dados de tipo para usar um mecanismo alternativo como uma propriedade de segura que gerencia o acesso isento ao campo subjacente.  Realize que os problemas como a contenção de bloqueio e os deadlocks podem afetar o desempenho e o comportamento de biblioteca.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se você estiver desenvolvendo um aplicativo e como consequência para ter controle total sobre o acesso ao tipo que contém o campo estático.  Os designers da biblioteca não devem omitir um aviso desta regra; usar campos estáticos de constante não pode fazer usando a biblioteca difícil para que os desenvolvedores a ser usada corretamente.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola esta regra.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]