---
title: "CA1053: os tipos de suporte est&#225;tico n&#227;o devem ter construtores | Microsoft Docs"
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
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1053: os tipos de suporte est&#225;tico n&#227;o devem ter construtores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo público aninhado declaram apenas membros estáticos e têm um construtor público ou protegido por padrão.  
  
## Descrição da Regra  
 O construtor é desnecessária porque chamar membros estáticos não requer uma instância do tipo.  Além disso, como o tipo não tem membros de não estático, criar uma instância não fornece acesso a qualquer um dos membros do tipo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o construtor padrão ou faça\-o privado.  
  
> [!NOTE]
>  Alguns compiladores criam automaticamente um construtor da opção do utilitário se o tipo não define nenhum construtores.  Se esse for o caso com seu tipo, adicione um construtor padrão particular para eliminar a violação.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  A presença do construtor sugere que o tipo não é um tipo estático.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola esta regra.  Observe que não há construtor padrão no código\-fonte.  Quando esse código é compilado em um assembly, o compilador C\# inserirá um construtor padrão, que viola esta regra.  Para corrigir isso, declarar um construtor privado.  
  
 [!CODE [FxCop.Design.StaticTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes#1)]