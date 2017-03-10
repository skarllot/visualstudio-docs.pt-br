---
title: "Compilador CS0444 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0444"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0444"
ms.assetid: 5beb8c06-39d3-4b59-a7c3-5590200bd43d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0444 de aviso (n&#237;vel 2)
Tipo predefinido ' nome do tipo 1' não foi encontrado no ' namespace System 1', mas foi encontrado em ' namespace System 2'  
  
 Um objeto predefinido como <xref:System.Int32> não foi encontrado onde o compilador espera encontrá\-lo, mas em vez disso, encontrado em ' namespace System 2'.  
  
 O erro pode indicar que o .NET Framework está instalado incorretamente. Para corrigir esse problema, reinstale o .NET Framework.  
  
 Se você estiver escrevendo suas próprias bibliotecas de classe base, você também pode encontrar esse erro. Nesse caso, para resolver o erro, recrie mscorlib.