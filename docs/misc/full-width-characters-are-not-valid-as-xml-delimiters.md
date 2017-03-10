---
title: "Caracteres de largura total n&#227;o s&#227;o v&#225;lidos como delimitadores XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31197"
  - "bc31197"
helpviewer_keywords: 
  - "BC31197"
ms.assetid: f5d724f8-545b-4cf8-9606-12c63814c6e8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Caracteres de largura total n&#227;o s&#227;o v&#225;lidos como delimitadores XML
Foi definido um literal XML que inclui um caractere de largura inteira como um delimitador. Caracteres de largura inteira são também conhecidos como caracteres largos ou de vários bytes.  
  
 **ID do erro:** BC31197  
  
### Para corrigir este erro  
  
-   Remova o caractere de largura inteira da definição de literais XML e substituí\-lo por um caractere delimitador de ANSI válido. Os caracteres delimitadores válidos incluem o seguinte: `<`, `>`, `=`, `:`, `/`.  
  
## Consulte também  
 [Literais XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Codificação de caracteres no .NET Framework](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)