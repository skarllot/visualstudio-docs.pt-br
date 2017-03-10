---
title: "Como: ler e gravar para a regi&#227;o de coment&#225;rios da barra de Status | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "região de comentários, barra de Status"
  - "Barra de status, região de comentários"
  - "Barra de status, visão geral"
ms.assetid: e639561c-e1e7-4660-b2a2-8bca80f34a29
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Como: ler e gravar para a regi&#227;o de coment&#225;rios da barra de Status
A região de comentários da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barra de status exibe o texto.  Você pode definir e recuperar texto, exibir texto estático e realçar o texto exibido.  
  
### Para usar a região de comentários da barra de Status de Visual Studio  
  
1.  Obter uma instância a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface, que é disponibilizado por meio do <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service.  
  
2.  Determinar se a barra de status está congelada chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> método da <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> instância.  
  
3.  Definir o texto da região comentários chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.SetText%2A> método e passando uma seqüência de texto.  
  
4.  Leia o texto da região de comentários, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> método.  
  
## Exemplo  
 Este exemplo demonstra como escrever o texto e ler texto da região de comentários.  
  
 [!code-cs[VSSDKFeedbackStatusBar#1](../misc/codesnippet/CSharp/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.cs)]
 [!code-vb[VSSDKFeedbackStatusBar#1](../misc/codesnippet/VisualBasic/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar_1.vb)]  
  
 No exemplo acima, o código faz o seguinte:  
  
-   Obtém uma instância da <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface da <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service.  
  
-   Verifica se a barra de status é congelada chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.IsFrozen%2A> método.  
  
-   Inibe outra atualização à barra de status chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> método.  
  
-   Lê o texto da barra de status chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.GetText%2A> método e o exibe em uma caixa de mensagem.  
  
-   Permite que as atualizações a barra de status chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.FreezeOutput%2A> e passando o parâmetro 0.  
  
-   Limpa o conteúdo da barra de status chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> método.  
  
## Consulte também  
 [Estendendo a barra de Status](../extensibility/extending-the-status-bar.md)   
 [Como: a barra de progresso do programa região da barra de Status](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Como: usar a região de animação da barra de Status](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Como: a região de Designer da barra de Status do programa](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)