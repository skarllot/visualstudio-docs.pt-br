---
title: "CA1032: implementar construtores de exce&#231;&#227;o padr&#227;o | Microsoft Docs"
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
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1032: implementar construtores de exce&#231;&#227;o padr&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo estende <xref:System.Exception?displayProperty=fullName> e não declara todos os construtores necessários.  
  
## Descrição da Regra  
 Os tipos de exceção devem implementar os seguintes construtores:  
  
-   NewException\(\)público  
  
-   NewException utilitário \(cadeia de caracteres\)  
  
-   NewException utilitário \(cadeia de caracteres, exceção\)  
  
-   NewException protegido ou particular \(SerializationInfo, StreamingContext\)  
  
 A falha ao fornecer o conjunto completo de construtores pode dificultar a tratar exceções corretamente.  Por exemplo, o construtor que tem a assinatura `NewException(string, Exception)` é usado para criar exceções causadas por outras exceções.  Sem este construtor você não pode criar e gerar uma instância da exceção personalizada que contém uma exceção aninhada \(\) interna, que é o que o código gerenciado deve fazer nessa situação.  Os três primeiros construtores de exceção são públicos por convenção.  O quarto construtor é protegido em classes não lacradas, e privada em classes seladas.  Para obter mais informações, consulte [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione os construtores ausentes exceto, e certifique\-se de que têm acessibilidade correta.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando a violação é causada usando um nível de acesso diferente para os construtores públicos.  
  
## Exemplo  
 O exemplo a seguir contém um tipo de exceção que viola esta regra e um tipo de exceção que é implementado corretamente.  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]