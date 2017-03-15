---
title: "CS0040 de erro do compilador | Microsoft Docs"
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
  - "CS0040"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0040"
ms.assetid: 6a600166-0335-4b6d-b050-6821b4624c96
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0040 de erro do compilador
Erro inesperado ao criar o arquivo de informações de depuração — 'razão'  
  
 Esse erro pode ocorrer ao usar o [\/Debug](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) opção de compilador e indica que o compilador não pôde gravar o arquivo. PDB. Possíveis resoluções para esse erro incluem reinstalando o Visual Studio, garantindo que o compilador tem acesso de gravação a um arquivo ou diretório ou não compilar com a opção \/debug.