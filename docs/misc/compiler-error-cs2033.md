---
title: "CS2033 de erro do compilador | Microsoft Docs"
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
  - "CS2033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2033"
ms.assetid: edb5784a-5195-4f72-b73d-d1ec9ed3766e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS2033 de erro do compilador
Não é possível criar nome de arquivo curto 'filename' quando já existe um arquivo longo com o mesmo nome de arquivo curto  
  
 Compile qualquer arquivo c\# com um nome mais de oito caracteres. Em seguida, compilar outro arquivo com a versão abreviada do nome do arquivo anterior, como os seis primeiros caracteres do nome mais "~ 1." O segundo compilar gerará esse erro.  
  
 Para resolver esse erro, renomeie o nome de arquivo curto para que não entrem em conflito com o nome de arquivo longo.