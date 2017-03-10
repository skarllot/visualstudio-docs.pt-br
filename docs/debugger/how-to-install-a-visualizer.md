---
title: "Como instalar um visualizador | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, visualizadores"
  - "visualizadores, instalando"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como instalar um visualizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Após ter criado um visualizador, você deverá instalar o visualizador de modo que esteja disponível em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Instalar um visualizador é um processo simples.  
  
> [!NOTE]
>  Nos aplicativos do **Store**, somente os visualizadores do texto padrão HTML, XML e JSON são suportados.  Não há suporte para visualizadores personalizados \(criados pelo usuário\).  
  
### Para instalar um visualizador  
  
1.  Localize a DLL que contém o visualizador que você criou.  
  
2.  Copie a DLL para qualquer um dos seguintes locais:  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Se você quiser usar um visualizador gerenciado para a depuração remota, copie a DLL no mesmo caminho no computador remoto.  
  
4.  Reinicie a sessão de depuração.  
  
## Consulte também  
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Como escrever um visualizador](../debugger/how-to-write-a-visualizer.md)