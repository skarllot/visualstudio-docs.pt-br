---
title: "CS1731 de erro do compilador | Microsoft Docs"
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
  - "CS1731"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1731"
ms.assetid: 267b32aa-a692-4a54-8654-0540ee36c0a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1731 de erro do compilador
Não é possível converter a expressão para delegar porque alguns dos tipos de retorno no bloco não são implicitamente conversíveis para o tipo de retorno do delegado.  
  
 Esse erro é gerado quando uma expressão lambda ou um método anônimo tem um tipo de retorno não é compatível com o tipo de retorno do delegado.  
  
### Para corrigir este erro  
  
1.  Altere o tipo de retorno do delegado ou a expressão.  
  
## Exemplo  
 O código a seguir gera CS1731:  
  
```  
class CS1731 { delegate double D(); D d = () => { return "Who knows the real sword of Gryffindor?"; }; }  
```