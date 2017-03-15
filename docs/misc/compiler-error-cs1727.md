---
title: "CS1727 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1727"
ms.assetid: 66478a58-e0f6-4886-b940-5473ad485a01
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1727 de erro do compilador
Não é possível enviar o relatório de erros automaticamente sem autorização. Visite ' para autorizar o envio de relatório de erros.  
  
 O site listado na mensagem de erro explica como habilitar o relatório de erros automático [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] Ferramentas de linha de comando.  
  
## Exemplo  
 O exemplo a seguir gera CS1727.  
  
```  
// CS1727.cs // compile with: /errorreport:send // CS1727 expected class Test { static void Main(){} }  
```  
  
## Consulte também  
 [\/errorreport \(Set Error Reporting Behavior\)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)