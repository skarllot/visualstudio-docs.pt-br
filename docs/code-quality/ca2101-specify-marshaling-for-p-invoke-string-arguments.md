---
title: "CA2101: especificar marshaling para argumentos da cadeia de caracteres P/Invoke | Microsoft Docs"
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
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2101: especificar marshaling para argumentos da cadeia de caracteres P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um membro da invocação de plataforma permitir chamadores parcialmente confiáveis, tem um parâmetro de cadeia de caracteres, e não faz explicitamente para realizar marshaling a cadeia de caracteres.  
  
## Descrição da Regra  
 Ao converter de Unicode para ANSI, é possível que nem todos os caracteres Unicode podem ser representados em uma página de código ANSI específica.  *o mapeamento de melhor ajuste* tenta resolver esse problema substituindo um caractere por caractere que não pode ser representado.  O uso desse recurso pode causar uma vulnerabilidade de segurança potencial porque você não pode controlar o caractere que é escolhido.  Por exemplo, o código mal\-intencionado pode intencionalmente criar uma cadeia de caracteres Unicode que contém os caracteres que não são encontrados em uma página de código específico, que são convertidos em caracteres especiais do sistema de arquivos como “.” ou “\/”.  Observe também que as verificações de segurança de caracteres especiais ocorrem frequentemente antes que a cadeia de caracteres é convertida em ANSI.  
  
 o mapeamento de melhor ajuste é o padrão para a conversão não gerenciado, WChar ao MByte.  A menos que você desabilitasse explicitamente o mapeamento de melhor ajuste, seu código pode conter uma vulnerabilidade de segurança explorável devido a esse problema.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, explicitamente tipos de dados de cadeia de caracteres de marshaling.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um método que viola essa regra, e depois mostra como corrigir a violação.  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]