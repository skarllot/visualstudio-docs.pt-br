---
title: "CS1617 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1617"
ms.assetid: fd3371ed-39eb-4d3d-b8f5-d96ac0c79398
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1617 de erro do compilador
Opção inválida 'option' \/langversion; deve ser ISO\-1, ISO\-2 ou padrão  
  
 Esse erro ocorre se você usou o [\/langversion](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option) configuração de comutador ou projeto de linha de comando mas não especificar uma opção de idioma válido. Para resolver esse erro, verifique a configuração de projeto ou sintaxe de linha de comando e altere\-o para uma das opções listadas.  
  
 Por exemplo, a compilação com `csc /langversion:ISO` irá gerar o erro CS1617.