---
title: "Como: usar a regi&#227;o de anima&#231;&#227;o da barra de Status | Microsoft Docs"
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
  - "Barra de status, programação"
  - "Barra de status, região de animação"
  - "região de animação, barra de Status"
ms.assetid: ec6fb915-7bc8-4a90-8156-70c1a243caff
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Como: usar a regi&#227;o de anima&#231;&#227;o da barra de Status
A região de animação da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barra de status exibe uma animação de looping que indica uma operação demorada ou uma operação de tamanho indeterminado \(por exemplo, a criação de vários projetos em uma solução\).  
  
### Para usar a região de animação da barra de status Visual Studio  
  
1.  Obter uma instância a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface, que é disponibilizado por meio do <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service.  
  
2.  Iniciar a animação, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> método da barra de status.  Passo 1 como o valor do primeiro parâmetro e uma referência a um ícone animado como o valor do segundo parâmetro.  
  
3.  Parar a animação chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Animation%2A> método da barra de status.  Passe 0 como o valor do primeiro parâmetro e uma referência para o ícone animado como o valor do segundo parâmetro.  
  
## Exemplo  
 Este exemplo demonstra como executar uma animação interna na região de animação.  
  
 [!CODE [VSSDKAnimationStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkanimationstatusbar#1)]  
  
## Consulte também  
 [Estendendo a barra de Status](../extensibility/extending-the-status-bar.md)   
 [Como: ler e gravar para a região de comentários da barra de Status](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Como: a barra de progresso do programa região da barra de Status](../misc/how-to-program-the-progress-bar-region-of-the-status-bar.md)   
 [Como: a região de Designer da barra de Status do programa](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)