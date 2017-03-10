---
title: "CA2241: fornecer argumentos corretos para m&#233;todos de formata&#231;&#227;o | Microsoft Docs"
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
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2241: fornecer argumentos corretos para m&#233;todos de formata&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 O argumento de cadeia de caracteres de `format` passado ao método como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, ou <xref:System.String.Format%2A?displayProperty=fullName> não contém um item de formato que corresponde a cada argumento do objeto, ou vice\-versa.  
  
## Descrição da Regra  
 Os argumentos para os métodos como <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, e <xref:System.String.Format%2A> consistem em uma cadeia de formato seguida por várias instâncias de <xref:System.Object?displayProperty=fullName> .  A cadeia de caracteres de formato consiste em texto e itens de formato inseridos do formulário, índice, alinhamento {\[\] \[: formatString\]}. os índices “é um inteiro baseado em zero que indica qual dos objetos no formato.  Se um objeto não tiver um índice correspondente na cadeia de caracteres de formato, o objeto será ignorado.  Se o objeto especificado por “índices não existir, <xref:System.FormatException?displayProperty=fullName> será gerado em tempo de execução.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, forneça um item de formato para cada argumento de objeto e fornecer um argumento de objeto para cada item de formato.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra duas violações da regra.  
  
 [!CODE [FxCop.Usage.FormattingArguments#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments#1)]