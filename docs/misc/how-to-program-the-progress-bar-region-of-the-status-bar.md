---
title: "Como: a barra de progresso do programa regi&#227;o da barra de Status | Microsoft Docs"
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
  - "Barra de status, região de barra de progresso"
  - "barra de progresso, barra de Status"
  - "Barra de status, programação"
ms.assetid: 4b54616a-8c20-436d-b764-f2380e5760f2
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Como: a barra de progresso do programa regi&#227;o da barra de Status
A região de barra de progresso da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] barra de status exibe o andamento incremental de rápida operações, por exemplo, salvando um arquivo em disco.  
  
### Para usar a região de barra de progresso da barra de status Visual Studio  
  
1.  Obter uma instância a <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface, que é disponibilizado por meio do <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service.  
  
2.  Inicializar a barra de progresso iniciando valores chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> método.  
  
3.  Atualizar a barra de progresso como sua operação continua usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> método para definir novos valores.  
  
## Exemplo  
 Este exemplo demonstra como inicializar e atualizar a barra de progresso.  
  
 [!CODE [VSSDKProgressStatusBar#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkprogressstatusbar#1)]  
  
 No exemplo, o código:  
  
-   Obtém uma instância da <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> interface da <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> service.  
  
-   Inicializa a barra de progresso para dada valores iniciais, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> método.  
  
-   Simula uma operação, iterando através de um `for` de loop e atualizar os valores da barra de progresso usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Progress%2A> método.  
  
-   Limpa a barra de progresso usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar.Clear%2A> método.  
  
## Consulte também  
 [Estendendo a barra de Status](../extensibility/extending-the-status-bar.md)   
 [Como: ler e gravar para a região de comentários da barra de Status](../misc/how-to-read-from-and-write-to-the-feedback-region-of-the-status-bar.md)   
 [Como: usar a região de animação da barra de Status](../misc/how-to-use-the-animation-region-of-the-status-bar.md)   
 [Como: a região de Designer da barra de Status do programa](../Topic/How%20to:%20Program%20the%20Designer%20Region%20of%20the%20Status%20Bar.md)