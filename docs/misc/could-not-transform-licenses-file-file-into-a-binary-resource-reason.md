---
title: "N&#227;o foi poss&#237;vel transformar o arquivo de licen&#231;as &#39;arquivo&#39; em um recurso bin&#225;rio. &lt; motivo &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel transformar o arquivo de licen&#231;as &#39;arquivo&#39; em um recurso bin&#225;rio. &lt; motivo &gt;
O processador de licenças usado para transformar arquivos. licx em recursos binários falhou por alguma razão.  
  
 Esse erro normalmente é causado por um arquivo. licx incorreta. Por exemplo, o arquivo pode foram aberto e modificado em um editor de texto.  
  
 O processo de compilação falhará se esse erro ocorrer.  
  
### Para corrigir este erro  
  
1.  Selecione o projeto no Solution Explorer.  
  
2.  Do **projeto** menu, clique em **Show All Files**.  
  
3.  No Solution Explorer, expanda a pasta obj e, em seguida, expanda o **Depurar** pasta.  
  
4.  Localize o arquivo chamado "myApplication.exe.licenses" onde myApplication é o nome do seu aplicativo de formulários do Windows.  
  
5.  Exclua o arquivo e recrie a solução.  
  
## Consulte também  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)