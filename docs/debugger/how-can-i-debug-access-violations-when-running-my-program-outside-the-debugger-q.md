---
title: "Como posso depurar viola&#231;&#245;es de acesso ao executar meu programa fora do depurador? | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depuração de violação de acesso"
  - "depurando [Visual Studio], violações de acesso"
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como posso depurar viola&#231;&#245;es de acesso ao executar meu programa fora do depurador?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrição do problema  
 Meu programa é executado corretamente no ambiente do Visual Studio, mas quando eu o executo em modo autônomo no sistema operacional Windows, ele gera uma violação de acesso.  Como posso depurar esse problema?  
  
## Solução  
 Defina a opção [Depuração Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md) e execute o programa de maneira autônoma até que a violação de acesso ocorra.  Em seguida, na caixa de diálogo **Violação de Acesso**, clique em **Cancelar** para iniciar o depurador.  
  
 Além disso, consulte o artigo da Base de Dados de Conhecimento Q133174, “Como localizar onde ocorre uma falha geral de proteção \(GP\)”. Os artigos da Base de Dados de Conhecimento podem ser encontrados no CD da Biblioteca MSDN ou pesquisando em [http:\/\/support.microsoft.com\/](http://support.microsoft.com/).  
  
## Consulte também  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)