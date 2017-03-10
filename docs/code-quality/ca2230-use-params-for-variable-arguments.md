---
title: "CA2230: usar par&#226;metros para argumentos vari&#225;veis | Microsoft Docs"
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
  - "UseParamsForVariableArguments"
  - "CA2230"
helpviewer_keywords: 
  - "CA2230"
  - "UseParamsForVariableArguments"
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2230: usar par&#226;metros para argumentos vari&#225;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo protegido contêm um público ou protegido um método que usa `VarArgs` que chama a convenção.  
  
## Descrição da Regra  
 `VarArgs` que chama a convenção é usado com certas definições do método que têm um número variável de parâmetros.  Um método que usa `VarArgs` que chama a convenção não é compatível CLS \(CLS\) e pode não estar acessível através das linguagens de programação.  
  
 No C\#, `VarArgs` que chama a convenção é usado quando a lista de parâmetros de um método termina com a palavra\-chave de `__arglist` .  Visual Basic não da suporte `VarArgs` que chama a convenção, e o Visual C\+\+ permite o uso apenas em código não gerenciado usando a notação de `...` de reticências.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra no C\#, use a palavra\-chave de [params](/dotnet/csharp/language-reference/keywords/params) em vez de `__arglist`.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra dois métodos, um que viola a regra e outro que obedece à regra.  
  
 [!code-cs[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## Consulte também  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)