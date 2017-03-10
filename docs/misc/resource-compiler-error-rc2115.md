---
title: "RC2115 de erro do compilador de recurso | Microsoft Docs"
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
  - "RC2115"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2115"
ms.assetid: 1b90feb0-f1fb-4f3c-8a9a-c44f9f8dc366
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# RC2115 de erro do compilador de recurso
cadeia de caracteres de texto ou ordinal esperado no controle  
  
 O *texto* campo de uma instrução de controle no **caixa de diálogo** instrução deve ser uma cadeia de caracteres de texto ou uma referência ordinal para o tipo de controle. Se usar um ordinal, verifique se você tem um `#define` instrução para o controle.