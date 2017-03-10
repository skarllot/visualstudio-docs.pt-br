---
title: "Instru&#231;&#245;es &#39;Line&#39; n&#227;o s&#227;o mais suportados (dispositivo inteligente/b&#225;sica compilador erro Visual) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30768"
  - "bc30768"
helpviewer_keywords: 
  - "BC30768"
ms.assetid: e7a17c77-06bb-4d33-966e-addb4f51caaf
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es &#39;Line&#39; n&#227;o s&#227;o mais suportados (dispositivo inteligente/b&#225;sica compilador erro Visual)
O `Line` instrução não é mais suportada. A funcionalidade de e\/s de arquivo geralmente está disponível como <xref:Microsoft.VisualBasic.FileSystem.LineInput%2A?displayProperty=fullName>, mas a versão de destino do .NET Compact Framework não oferece suporte a ele.  
  
 **ID do erro:** BC30768  
  
### Para corrigir este erro  
  
-   Se executar o acesso a arquivos, use as funções definidas no <xref:System.IO> namespace.  
  
-   Se executar gráficos, use <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>.  
  
## Consulte também  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [Access de arquivo com o Visual Basic](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/file-access)