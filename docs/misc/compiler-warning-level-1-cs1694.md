---
title: "Compilador CS1694 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1694"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1694"
ms.assetid: 9cb6b5d4-36a0-4b07-9690-14b5105da44b
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1694 de aviso (n&#237;vel 1)
Nome de arquivo inválido especificado para diretiva de pré\-processamento. Nome do arquivo é muito longo ou não um nome de arquivo válido.  
  
 Este aviso ocorre ao usar o `#pragma checksum` diretiva de pré\-processamento. O nome de arquivo especificado tem mais de 256 caracteres. Para resolver esse aviso, use um nome de arquivo mais curto.  
  
## Exemplo  
 O exemplo a seguir gera CS1694.  
  
```  
// cs1694.cs #pragma checksum "MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890MyFile1234567890.txt" {00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F}   // CS1694 class MyClass {}  
```