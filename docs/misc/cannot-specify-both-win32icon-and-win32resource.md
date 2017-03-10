---
title: "N&#227;o &#233; poss&#237;vel especificar /win32icon e /win32resource | Microsoft Docs"
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
  - "vbc2023"
  - "bc2023"
helpviewer_keywords: 
  - "BC2023"
ms.assetid: 60914807-1fde-4fef-9c6f-6f4a62527eed
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel especificar /win32icon e /win32resource
O `/win32resource` e `/win32icon` são mutuamente exclusivas, porque as duas inserem informações de ícone no arquivo de saída.  
  
 **ID do erro:** BC2023  
  
### Para corrigir este erro  
  
-   Use somente o `/win32icon` opção para inserir um arquivo. ico no arquivo de saída. Esse arquivo. ico representa o arquivo de saída no Windows Explorer.  
  
     – ou –  
  
-   Use somente o `/win32resource` opção para inserir um arquivo de recurso Win32 no arquivo de saída. Um recurso do Win32 pode conter versão ou bitmap informações \(ícone\) que ajudam a identificar seu aplicativo no Windows Explorer.  
  
## Consulte também  
 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)   
 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)