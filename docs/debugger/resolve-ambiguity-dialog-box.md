---
title: "Caixa de di&#225;logo Resolver Ambiguidade | Microsoft Docs"
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
  - "vs.debug.Disambig"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, Caixa de diálogo Resolver Ambiguidade"
  - "depurando [C++], resolvendo ambiguidade"
  - "Caixa de diálogo Resolver Ambiguidade"
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Resolver Ambiguidade
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A caixa de diálogo `Resolve Ambiguity` aparece quando o depurador não pode escolher o local para exibir.  Por exemplo, se você estiver usando modelos C\+\+, poderá criar várias funções de um único modelo da função.  Se o depurador para em um local de origem no modelo, e você escolher `Go To Disassembly`, o depurador tem várias opções.  Cada função criada do modelo tem seu próprio código de desmontagem, e o depurador não sabe qual código você deseja exibir.  A caixa de diálogo `Resolve Ambiguity` permite que você selecione o local desejado de uma lista de todos os locais correspondentes.  
  
 `Choose the specific location`  
 Lista todos os lugares que correspondem ao comando.  
  
 `Address`  
 Mostra os endereços de memória para cada função.  
  
 `Function`  
 Mostra o nome de cada função.  
  
 `Module`  
 Mostra o módulo \(EXE ou DLL\) que contém o código de objeto para a função.  
  
## Consulte também  
 [Expressões no depurador](../debugger/expressions-in-the-debugger.md)