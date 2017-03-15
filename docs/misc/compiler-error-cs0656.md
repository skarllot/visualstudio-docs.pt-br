---
title: "CS0656 de erro do compilador | Microsoft Docs"
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
  - "CS0656"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0656"
ms.assetid: e695280a-e75d-4e8c-aec2-1f3fb455544a
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0656 de erro do compilador
Compilador ausente necessárias membro 'object.member'  
  
 Um dos problemas a seguir exista:  
  
-   A instalação do common language runtime está corrompida.  
  
-   Você tem uma referência a um assembly que define um tipo que também se encontra no common language runtime. No entanto, tipo do assembly não está definido para o modo de espera que o compilador c\#.  
  
 Verifique as referências para garantir que você está usando a versão correta do common language runtime.