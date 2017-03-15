---
title: "N&#227;o foi poss&#237;vel obter o nome do sistema completo de opera&#231;&#227;o devido a erro interno | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrDiagnosticInfo_FullOSName"
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o foi poss&#237;vel obter o nome do sistema completo de opera&#231;&#227;o devido a erro interno
Não foi possível obter o nome do sistema completo de operação devido a erro interno. Isso pode ser causado pelo WMI não existentes no computador atual.  
  
 Uma chamada para o `My.Computer.Info.OSFullName` propriedade falhou. Uma possível causa dessa falha é se o Windows Management Instrumentation \(WMI\) não está instalado no computador atual.  
  
### Para corrigir este erro  
  
1.  Adicionar um `Try...Catch` em torno da chamada para o `My.Computer.Info.OSFullName` propriedade.  
  
2.  Para obter mais informações sobre WMI e como instalá\-lo, vá para  e procure "Windows Management Instrumentation Core".  
  
## Consulte também  
 [Propriedade My.Computer.Info.OSFullName](http://msdn.microsoft.com/pt-br/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)   
 [Exceção e tratamento de erros no Visual Basic](http://msdn.microsoft.com/pt-br/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)