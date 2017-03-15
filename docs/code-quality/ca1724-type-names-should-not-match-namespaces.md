---
title: "CA1724: os nomes de tipo n&#227;o devem corresponder a namespaces | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1724: os nomes de tipo n&#227;o devem corresponder a namespaces
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um nome de tipo corresponder nomes de um namespace de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] em uma comparação sem diferenciação de maiúsculas e minúsculas.  
  
## Descrição da Regra  
 Os nomes de tipo não devem corresponder aos nomes de namespaces que são definidas na biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .  Violar esta regra pode reduzir a usabilidade de biblioteca.  
  
## Como Corrigir Violações  
 Selecione um nome de tipo que não corresponde ao nome de um namespace da biblioteca de classes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] .  
  
## Quando Suprimir Alertas  
 Para desenvolvimento, nenhum cenário conhecido ocorre quando você precisar eliminar um aviso desta regra.  Antes de você suprimir o aviso, considere atentamente como os usuários da biblioteca podem ser confundidas por nome correspondente.  Para enviar bibliotecas, você pode precisar eliminar um aviso desta regra.