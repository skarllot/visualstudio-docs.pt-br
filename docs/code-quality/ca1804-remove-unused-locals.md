---
title: "CA1804: remover locais n&#227;o usados | Microsoft Docs"
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
  - "CA1804"
  - "RemoveUnusedLocals"
helpviewer_keywords: 
  - "RemoveUnusedLocals"
  - "CA1804"
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1804: remover locais n&#227;o usados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método declara uma variável local mas não usa a variável exceto possivelmente como o destinatário da instrução de atribuição.  Para análise por esta regra, o assembly deve ser testado compilado com informações de depuração e o arquivo associado de base de dados do programa \(.pdb\) deve estar disponível.  
  
## Descrição da Regra  
 As variáveis locais não usado e as atribuições desnecessários aumenta o tamanho de um desempenho do assembly e a diminuição.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remover ou usar variável local.  Observe que o compilador C\# que é incluído com [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] remove as variáveis locais não usado quando a opção de `optimize` está habilitada.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se a variável foi compilador emissor.  Também é seguro suprimir um aviso desta regra, ou desabilitar a regra, se o desempenho e a manutenção do código não são principais preocupações.  
  
## Exemplo  
 O exemplo a seguir mostra várias variáveis locais não usado.  
  
 [!CODE [FxCop.Performance.UnusedLocals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals#1)]  
  
## Regras Relacionadas  
 [CA1809: evitar locais excessivos](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: evitar classes internas sem instâncias](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: revisar parâmetros não usados](../Topic/CA1801:%20Review%20unused%20parameters.md)