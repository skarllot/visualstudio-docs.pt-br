---
title: "CA1300: especificar MessageBoxOptions | Microsoft Docs"
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
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300: especificar MessageBoxOptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Categoria|Microsoft.Globalization|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método chama uma sobrecarga do método de <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> que não usa um argumento de <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> .  
  
## Descrição da Regra  
 Para exibir uma caixa de mensagem corretamente para as culturas que usam uma ordem da direita para a esquerda de leitura, <xref:System.Windows.Forms.MessageBoxOptions> e membros de <xref:System.Windows.Forms.MessageBoxOptions> de enumeração de <xref:System.Windows.Forms.MessageBoxOptions> deve ser passado ao método de <xref:System.Windows.Forms.MessageBox.Show%2A> .  Examine a propriedade de <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> de controle contentor para determinar se usar uma ordem da direita para a esquerda de leitura.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame uma sobrecarga do método de <xref:System.Windows.Forms.MessageBox.Show%2A> que usa um argumento de <xref:System.Windows.Forms.MessageBoxOptions> .  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra quando a biblioteca de código não será localizada de uma cultura que usa uma ordem da direita para a esquerda de leitura.  
  
## Exemplo  
 O exemplo a seguir mostra um método que exibe uma caixa de mensagem com as opções que são apropriados para a ordem de leitura da cultura.  Um arquivo de recursos, que não é mostrado, é necessário criar o exemplo.  Siga os comentários no exemplo para criar o exemplo sem um arquivo de recurso e para testar o recurso da direita para a esquerda.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## Consulte também  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Recursos em aplicativos de área de trabalho](../Topic/Resources%20in%20Desktop%20Apps.md)