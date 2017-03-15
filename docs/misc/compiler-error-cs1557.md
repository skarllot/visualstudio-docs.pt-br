---
title: "CS1557 de erro do compilador | Microsoft Docs"
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
  - "CS1557"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1557"
ms.assetid: 1615e028-aeb7-4788-bd87-8e49e502d698
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1557 de erro do compilador
Não é possível usar 'class' para o método Main porque está em um arquivo de saída diferente  
  
 O [\/principal](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) opção de compilador foi especificada para um arquivo em uma compilação de saída de vários arquivos de saída. No entanto, a classe não foi encontrada no código\-fonte para o \/main compilação; foi localizado em um arquivo de código fonte para um dos outros arquivos de saída de compilação.