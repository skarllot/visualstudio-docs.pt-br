---
title: "Como exibir documentos de script | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
helpviewer_keywords: 
  - "Gerenciador de Script"
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como exibir documentos de script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Em versões anteriores do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor eram exibidos na janela Explorador de Script.  A janela Explorador de Script estava geralmente oculta, de modo que a disponibilidade de script do lado do cliente não era sempre óbvia.  
  
 No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor aparecem no Gerenciador de Soluções, que é visível por padrão.  A janela Explorador de Script foi eliminada.  
  
 Os arquivos de script do lado do cliente são visíveis apenas quando você está no modo de depuração ou modo de interrupção.  Eles aparecem no nó **Documentos de Script**.  
  
 Os arquivos de script do lado do servidor são sempre visíveis.  Eles aparecem no nó **\<Nome do caminho do site\>**.  O nome do nó é semelhante a este exemplo: `c:\...\Website2\`  
  
### Para exibir um documento de script do lado do servidor  
  
1.  No **Gerenciador de Soluções**, abra o nó **\<Nome do caminho do site\>**.  
  
2.  Clique duas vezes no arquivo de script que deseja exibir.  
  
     O arquivo de script do lado do servidor é aberto em uma janela de origem.  
  
### Para exibir um documento de script do lado do cliente  
  
1.  No **Gerenciador de Soluções**, abra o nó **Documentos de Script**.  
  
2.  Clique duas vezes no arquivo de script que deseja exibir.  
  
     O arquivo de script do lado do cliente é aberto em uma janela de origem.  
  
## Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)