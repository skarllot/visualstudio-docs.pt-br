---
title: "CA2232: marcar pontos de entrada dos Windows Forms com STAThread | Microsoft Docs"
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
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2232: marcar pontos de entrada dos Windows Forms com STAThread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um assembly faz referência ao namespace de <xref:System.Windows.Forms> , e seu ponto de entrada não é marcado com o atributo de <xref:System.STAThreadAttribute?displayProperty=fullName> .  
  
## Descrição da Regra  
 <xref:System.STAThreadAttribute> indica que o modelo de threading COM para o aplicativo é STA. de thread único.  Esta deverá de atributo estiver presente no ponto de entrada de qualquer aplicativo que usa o Windows Forms; se for omitida, os componentes do windows podem não funcionar corretamente.  Se o atributo não estiver presente, o aplicativo usa o modelo multi\-threaded STA. do, que não tem suporte no Windows Forms.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projetos que usa a estrutura de aplicativo não precisa marcar o método de**Principal** com STAThread.  O compilador de[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] faz automaticamente.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione o atributo de <xref:System.STAThreadAttribute> ao ponto de entrada.  Se o atributo de <xref:System.MTAThreadAttribute?displayProperty=fullName> estiver presente, removê\-lo.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se você está desenvolvendo para .NET Compact Framework, para que o atributo de <xref:System.STAThreadAttribute> é desnecessário e não tiver suporte.  
  
## Exemplo  
 Os exemplos a seguir demonstram o uso correto de <xref:System.STAThreadAttribute>.  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]