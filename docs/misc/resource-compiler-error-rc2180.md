---
title: "RC2180 de erro do compilador de recurso | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RC2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2180"
ms.assetid: 6d296138-7989-491e-a45b-6c3a4743116a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# RC2180 de erro do compilador de recurso
não é possível abrir o arquivo temporário  
  
 O recurso de compilador\/Visual C\+\+ não pôde abrir um arquivo temporário. A causa provável é que você não tem permissões de gravação para o diretório ou o diretório não existe. O recurso de compilador\/Visual C\+\+ tenta usar esses arquivos no diretório especificado pelo **TMP** variável de ambiente ou o diretório atual, se nenhum for especificado.