---
title: "n&#227;o &#233; poss&#237;vel enviar o relat&#243;rio de erros automaticamente | Microsoft Docs"
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
  - "bc2027"
  - "vbc2027"
helpviewer_keywords: 
  - "BC2027"
ms.assetid: 84ba8580-2234-46d1-b4a5-94b03f64c0c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# n&#227;o &#233; poss&#237;vel enviar o relat&#243;rio de erros automaticamente
não é possível enviar o relatório de erros automaticamente. Visite 'http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039' para configurar envio erro configurações de relatório.  
  
 Você especificou o `/errorreport:send` opção de compilador, mas o computador não está configurado para enviar automaticamente relatórios de erro. Nenhuma informação será enviada sobre erros internos no compilador do Visual Basic.  
  
 **ID do erro:** BC2027  
  
### Para corrigir este erro  
  
-   Remover o `/errorreport:send` compilador opção ou substituí\-lo por `/errorreport:queue`, `/errorreport:prompt`, ou `/errorreport:none`.  
  
     – ou –  
  
-   Habilitar o relatório seguindo as instruções em erros automático [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039).  
  
## Consulte também  
 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)   
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039)