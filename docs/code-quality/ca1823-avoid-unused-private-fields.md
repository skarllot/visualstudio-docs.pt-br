---
title: "CA1823: evitar campos privados n&#227;o usados | Microsoft Docs"
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
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1823: evitar campos privados n&#227;o usados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Esta regra é informada quando um campo privado em seu código existe mas não é usada por nenhum caminho de código.  
  
## Descrição da Regra  
 Os campos particulares foram detectados que não parece ser acessados no assembly.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o campo ou adicione o código que o usa.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra.  
  
## Regras Relacionadas  
 [CA1812: evitar classes internas sem instâncias](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: revisar parâmetros não usados](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)