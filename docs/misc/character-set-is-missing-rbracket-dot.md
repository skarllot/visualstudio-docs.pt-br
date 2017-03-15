---
title: "&#39;]&#39; est&#225; ausente no conjunto de caracteres. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_SETMISSINGCLOSE"
  - "vs.message.0x800A00C0"
ms.assetid: 97d2436c-498d-4eb0-a08c-8efcc7797fc0
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &#39;]&#39; est&#225; ausente no conjunto de caracteres.
Esse erro geralmente ocorre quando o fechamento colchete \(`]`\) está ausente para uma expressão regular especificada em uma localização ou substituir a cadeia de caracteres.  
  
### Para corrigir este erro  
  
1.  Para localizar o caractere literal `]`, use `\]`.  
  
2.  Para corresponder a um conjunto de caracteres, insira o suporte ausente `]`.  
  
## Consulte também  
 [Usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Localizar e substituir, localização rápida](http://msdn.microsoft.com/pt-br/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Localizar nos arquivos](../ide/find-in-files.md)