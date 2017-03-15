---
title: "&lt; nome &gt; n&#227;o &#233; um nome de arquivo v&#225;lido. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt; nome &gt; n&#227;o &#233; um nome de arquivo v&#225;lido.
Esse erro ocorre quando você tenta criar um novo arquivo na janela de comando, mas incluir caracteres sem suporte no nome do arquivo.  
  
 Nomes de arquivo não podem conter os seguintes caracteres:  
  
-   libra \(\#\)  
  
-   porcentagem \(%\)\)  
  
-   e comercial \(&\)  
  
-   asterisco \(\*\)  
  
-   barra vertical \(&#124;\)  
  
-   barra invertida \(\\\)  
  
-   dois\-pontos \(:\)  
  
-   aspas duplas \("\)  
  
-   menor que \(\<\)  
  
-   maior que \(\>\)  
  
-   ponto \(.\)  
  
-   ponto de interrogação \(?\)  
  
-   barra \(\/\)  
  
-   espaços iniciais ou finais \(' '\)  
  
-   nomes reservados do Windows ou DOS \(nul, aux, con, com1, lpt1 e assim por diante\)  
  
### Para corrigir este erro  
  
-   Digite o comando com um novo nome de arquivo que contém os caracteres listados acima.  
  
## Consulte também  
 [Comando Novo Arquivo](../ide/reference/new-file-command.md)   
 [Comandos do Visual Studio](../ide/reference/visual-studio-commands.md)